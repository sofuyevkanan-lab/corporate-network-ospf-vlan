# 🌐 Enterprise Network Lab: VLANs & OSPF Routing

## 📌 What's this project about?
I built this Cisco Packet Tracer lab to get some hands-on practice with L2 switching and L3 dynamic routing. The main goal was to connect a Core and a Branch office while making sure different departments (like Finance and Software) stay logically separated. 

It was a great way to put CCNA concepts into practice rather than just reading about them!

## 🛠 Tech Stack & Protocols Used
* **VLANs & 802.1Q Trunking:** To isolate department traffic securely[cite: 1, 2].
* **Router-on-a-Stick:** To allow routing between the different VLANs[cite: 1].
* **OSPFv2 (Single Area):** Configured a Point-to-Point (PtP) link between the Core and Branch routers so they can share routes dynamically[cite: 2, 3].
* **STP & PortFast:** To prevent Layer 2 broadcast storms and bring end-user ports up instantly[cite: 1, 3].

## 📊 IP Subnetting Breakdown
| Network | CIDR | Subnet Mask | Default Gateway |
| :--- | :--- | :--- | :--- |
| VLAN 10 (Finance) | 192.168.10.0/24 | 255.255.255.0 | 192.168.10.1 |
| VLAN 20 (Software) | 192.168.20.0/24 | 255.255.255.0 | 192.168.20.1 |
| PtP WAN Link | 10.0.0.0/30 | 255.255.255.252 | N/A |

## ✅ Proof it works!
To make sure everything is working, I verified the routing tables. Here is the CLI output showing that the router successfully formed an OSPF adjacency and learned the routes (notice the `O` flag):

```text
Router(config)#do show ip route ospf
O     192.168.10.0 [110/2] via 10.0.0.1, 00:00:23, GigabitEthernet0/0/1
O     192.168.20.0 [110/2] via 10.0.0.1, 00:00:23, GigabitEthernet0/0/1
