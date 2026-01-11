# Test Configuration Documentation

**Project:** HealthConnect Architecture Comparison
**Test ID:** HC-SIM-20260111-001
**Date:** January 11, 2026
**Duration:** 12 hours continuous
**Author:** RHIBA Zakaria

---

## Overview

This document provides comprehensive specifications for the HealthConnect telemedicine architecture comparison test. The test evaluated four distinct architectures (Lambda, MQTT, CoAP, HTTP) under identical conditions to determine optimal performance for real-time vital sign monitoring.

---

## Test Environment

### Hardware Infrastructure

#### IoT Simulation Layer
- **Devices**: 10× Raspberry Pi 4 Model B
- **CPU**: Broadcom BCM2711 Quad-core @ 1.5GHz
- **RAM**: 4GB LPDDR4-3200 per device
- **Patients per Device**: 10 (total 100 simulated patients)

#### Server Infrastructure (Lambda Architecture)
- **Kafka Cluster**: 3 nodes (8-core, 16GB RAM, 512GB SSD each)
- **Spark Cluster**: 1 master + 3 workers (8-core, 16GB RAM each)
- **MongoDB**: 3-node replica set (8-core, 32GB RAM, 1TB SSD each)

### Software Stack

| Component | Version | Purpose |
|-----------|---------|---------|
| Apache Kafka | 3.3.1 | Message broker |
| Apache Spark | 3.3.0 | Stream processing |
| MongoDB | 5.0.3 | Database |
| Python | 3.9.7 | Application logic |

---

## Test Parameters

- **Duration**: 12 hours (43,200 seconds)
- **Patients**: 100
- **Sampling Rate**: 10 Hz
- **Total Events**: 43,200,000
- **Load**: 1,000 events/second (sustained)

### Vital Sign Distributions

| Vital Sign | Mean | Std Dev | Range |
|------------|------|---------|-------|
| Heart Rate | 82 bpm | 5 | [60, 120] |
| SpO2 | 98% | 1 | [85, 100] |
| Temperature | 37.0°C | 0.3 | [36.5, 39.5] |

### Anomalies: 5% total (1.7% each type)

---

## Results Summary

| Architecture | Mean Latency | Data Loss | Throughput |
|--------------|--------------|-----------|------------|
| Lambda | 185 ms | 0% | 500K/s |
| MQTT | 420 ms | 0.8% | 50K/s |
| CoAP | 510 ms | 1.2% | 30K/s |
| HTTP | 780 ms | 2.3% | 1K/s |

---

**Contact**: zakariarhiba21@gmail.com
