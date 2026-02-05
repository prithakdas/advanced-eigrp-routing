# Advanced EIGRP Routing

## Overview
This project demonstrates the implementation of **advanced EIGRP routing concepts** using Cisco routers in a controlled lab environment. The focus of this project is on **routing behavior and optimization**, rather than end-host connectivity, by using loopback interfaces and point-to-point serial links.

The lab showcases how EIGRP can be enhanced using **manual route summarization**, **authentication**, and **unequal load balancing** to build a secure and efficient routing topology.

---

## Project Objective
The objective of this project is to design and implement an **EIGRP-based routing environment** to demonstrate key advanced routing concepts, including:

- Manual route summarization  
- EIGRP authentication  
- Unequal load balancing  

The project emphasizes:
- Controlled route advertisement  
- Secure EIGRP neighborships  
- Optimized traffic flow using **metric manipulation and variance**

---

## Topology Summary
- Total routers: **7**
- Connectivity: **Serial point-to-point links**
- Loopback interfaces used to represent networks
- No end devices (PCs or switches) included to keep the focus purely on routing

Key design elements:
- **Authenticated path** using 30.0.0.4/30
- **Alternate path** using 50.0.0.0/30  
- **Summarized routing table** demonstrated on Router6 and compared with Router7  

---

## Technologies Used
- Routing Protocol: **EIGRP (AS 1)**
- Simulation Tool: **Cisco Packet Tracer**
- Routing concepts implemented:
  - Manual route summarization
  - MD5 authentication
  - Metric manipulation (delay)
  - EIGRP variance for unequal load balancing

---

## Configuration Highlights

### EIGRP Configuration
- EIGRP enabled on all routers using **AS 1**
- Unique **router IDs** configured
- `no auto-summary` enabled on all routers

---

### Manual Route Summarization
Manual route summarization is configured on **Router5** and applied on outbound interfaces to reduce routing table size.

Summarized networks:
- `56.12.16.0/22`
- `30.0.0.0/28`
- `50.0.0.0/29`
- `60.0.0.0/29`

Verification:
- Router6 shows a **reduced routing table**
- Router7 shows the **unsummarized routing table** for comparison

---

### EIGRP Authentication
- Authentication configured **only between Router2 and Router4**
- MD5 authentication using key chains
- Authentication applied at the **interface level**

This ensures:
- Secure EIGRP neighborship
- Protection against unauthorized routing updates

---

### Unequal Load Balancing
Unequal load balancing is implemented **at Router2** between two paths:

- **Authenticated path (30.0.0.4/30)** → Preferred path (Successor)
- **Alternate path (50.0.0.0/30)** → Less preferred path (Feasible Successor)

Implementation steps:
1. Increased delay on the alternate (50.0.0.0/30) path
2. Verified successor and feasible successor in the EIGRP topology table
3. Applied `variance 2` under EIGRP configuration

Result:
- Traffic is distributed across both paths
- More traffic flows through the preferred authenticated path

---

## Verification Commands
The following commands were used to verify the configuration:
show ip eigrp neighbors
show ip eigrp topology
show ip route
show running-config

Verification confirms:
- Stable EIGRP neighborships
- Successful route summarization
- Secure authentication
- Unequal load balancing functionality

---

## Repository Contents
- `Advanced_EIGRP_Routing_Topology.pkt` – Packet Tracer topology file  
- `Advanced-EIGRP-Routing-Report.pdf` – Detailed project report with configurations and screenshots  
- `README.md` – Project overview and documentation  

---

## Key Learning Outcomes
- Understanding EIGRP metric calculation and path selection
- Implementing manual route summarization
- Securing EIGRP using authentication
- Applying unequal load balancing using EIGRP variance

---

## Conclusion
This project demonstrates how advanced EIGRP features can be combined to build a **secure, scalable, and optimized routing environment**. The lab reflects real-world routing design considerations and provides a strong foundation for further exploration of dynamic routing protocols.
