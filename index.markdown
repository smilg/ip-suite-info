---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: home
---

## Ethernet Communications: A Guide to Ethernet standards and How they Function

### Introduction to Gigabit Ethernet
In the realm of Ethernet communications, the Gigabit Ethernet standard, specifically the 1000BASE-T (IEEE 802.3ab), is predominantly used for the devices we rely on everyday. This standard ensures efficient and reliable data transmission across networks.

### Key Specifications of 1000BASE-T
1. **Cable Requirements**: 1000BASE-T requires the use of Category 5 (or higher) cables, supporting frequencies up to 100 MHz. These cables are made of four twisted pairs used for differential signaling, typically terminated with an 8P8C connector. This connector is often confused with the RJ45 connector.
2. **Termination Schemes**: Two common termination schemes, T568A and T568B, can be used interchangeably in an installation, provided the same scheme is used at both ends (creating a "straight-through" cable). A crossover cable, necessary for certain connections, is created by using different terminations on each end.
3. **Balanced Lines**: These lines are crucial for maintaining high Signal-to-Noise Ratio (SNR) amidst interference and crosstalk.
4. **Port Types**: Ethernet devices feature two types of ports: MDI and MDI-X (with X denoting internal crossover). Most modern devices incorporate auto MDI-X, automatically adjusting for crossover requirements.
5. **Data Transmission**: 1000BASE-T utilizes all four pairs for bidirectional communication, using hybrid circuits and cancellers. It employs 4D-PAM5 encoding, where "4D" signifies each wire pair as one dimension and "PAM5" stands for five-level pulse amplitude modulation.

![Ethernet cabling Diagram](imgs/ETHCABLES.jpg)

### Understanding Ethernet Standards
- **Generations of Ethernet**: Ethernet has evolved through four generations - Standard Ethernet (10 Mbps), Fast Ethernet (100 Mbps), Gigabit Ethernet (1 Gbps), and 10 Gigabit Ethernet (10 Gbps). Each generation has built upon the foundational features of its predecessors.
- **Key Features of Standard Ethernet**: This form of Ethernet, now largely unused, was characterized by its 'connectionless' and 'unreliable' service, meaning frames were sent independently and the sender was unaware of any dropped frames.
#### Fast Ethernet (100 Mbps)
Fast Ethernet, offering a data rate of 100 Mbps, was designed to be compatible with the Standard Ethernet while significantly increasing the speed. It maintains the same 48-bit addressing and frame format as Standard Ethernet.

- **MAC Layer Consistency**: The Media Access Control (MAC) layer remains unchanged, allowing the frame format, as well as the minimum and maximum frame sizes, to stay the same.
- **Collision Detection**: With the increased speed, CSMA/CD (Carrier Sense Multiple Access with Collision Detection) had to be adapted. Collision detection became 10 times more sensitive to accommodate the higher data rate.
- **Topology Shift**: The traditional bus topology was replaced with a star topology, using a passive hub or a switch as the central point. The maximum cable length was adjusted to 250 meters, down from 2500 meters in standard Ethernet, for compatibility reasons.
- **Switches and Full-Duplex**: Fast Ethernet introduced switches with buffers for storing frames. Full-duplex connections allowed private transmission mediums for each host, eliminating the need for CSMA/CD.
- **Autonegotiation**: This feature enabled devices with different speeds (e.g., 10 Mbps and 100 Mbps) to communicate by automatically negotiating the data rate.
- **Encoding Techniques**: Fast Ethernet utilized various encoding schemes. 100Base-TX used two twisted pairs with 4B/5B block coding for synchronization. 100Base-FX employed fiber-optic cables, and there was also 100Base-T4.

#### Gigabit Ethernet (1 Gbps)
Gigabit Ethernet was developed to maintain compatibility with both standard and fast Ethernet, keeping the same address length, frame format, and frame size.

- **Duplex Modes**: The specification included both half and full-duplex modes, but modern implementations predominantly use full-duplex with switches.
- **Switches and No Collisions**: With a central switch connecting all computers, collisions were eliminated, making CSMA/CD unnecessary. The maximum cable length was then limited by signal attenuation rather than the collision detection process.
- **Topology and Wiring**: Gigabit Ethernet can use either a two-wire or four-wire implementation. The two-wire variant typically uses fiber-optic cables (1000Base-SX or 1000Base-LX), while the four-wire version uses Category 5 twisted pair cables (1000Base-T).
- **Encoding**: The high bandwidth requirements meant traditional Manchester encoding was unsuitable. The two-wire system used NRZ and other complex encoding systems, while the four-wire system employed 4D-PAM5.

#### 10 Gigabit Ethernet
10 Gigabit Ethernet, while not as widely adopted initially, represented a significant leap in data rate capabilities. It was designed to facilitate the interconnection of LANs, MANs, and WANs.

- **Continuity in Frame Structure**: This standard retained the frame size and format of its predecessors.
- **Implementation and Duplex Mode**: Most implementations used fiber-optic cables due to the difficulty in achieving such high data rates with copper. The standard operates exclusively in full-duplex mode.

### Ethernet Frame Structure
![Figure depicting standard ethernet frame](imgs/ETHFRAME.jpg)
1. **Preamble and SFD**: The preamble is a 7-byte sequence of alternating 1s and 0s, signaling an incoming frame. The SFD (Start Frame Delimiter) indicates the imminent start of the frame.
2. **Addresses**: Frames contain a 6-byte Destination Address (DA) and a 6-byte Source Address (SA), identifying the recipient and sender, respectively.
3. **Type and Data**: The 'Type' field specifies the upper-layer protocol, while the 'Data' section carries the encapsulated data.
4. **CRC**: The Cyclic Redundancy Check (CRC) is used for error detection.
5. **Frame Length**: Ethernet frames have a minimum length of 512 bits and a maximum payload length of 1500 bytes.

### Device Connection Methods in Ethernet Networks

#### Hubs
Hubs are basic networking devices that operate only at the physical layer. They are no longer widely used in modern networks due to their limitations.

- **Functionality**: Hubs function as multiport repeaters in a star topology. They regenerate and broadcast incoming frames to all ports except the one they were received on, effectively broadcasting the frame to all connected devices.
- **Limitations**: Hubs do not process link-layer addresses and cannot determine the specific destination port for a frame. All devices on the network receive the frame, but only the intended recipient processes it, while others discard it. This "dumb" approach leads to inefficiencies and security concerns.

#### Link-Layer Switches
Switches operate at both the physical and data-link layers, offering more intelligence and efficiency than hubs.

- **Signal Regeneration**: Like hubs, switches regenerate the received signal at the physical layer to maintain signal integrity.
- **Frame Filtering and Forwarding**: At the data-link layer, switches inspect MAC addresses in frames. They send frames only to the port connected to the intended recipient, reducing unnecessary network traffic and increasing security.
- **Transparent Switches**: These switches are invisible to network stations (stations are unaware of the switch's presence), simplifying network configuration and maintenance. IEEE 802.1d standard outlines criteria for transparent switches, including frame forwarding, dynamic address learning, and loop prevention.
- **Dynamic Address Learning**: Switches build a forwarding table by learning from frame movements, mapping MAC addresses to corresponding ports. This process is automatic but may take time as the switch learns the network's layout.
- **Loop Prevention**: Redundant switches are favored for reliability but can create loops. Special protocols are used to prevent looping and ensure network stability.

#### Advantages of Switches over Hubs
- **Collision-Free**: Switches eliminate collisions, improving the available bandwidth for each host.
- **Versatility**: They can interconnect devices using different physical layer protocols and media types, as long as the data-link layer frame format remains the same.

#### Routers
Routers are more advanced devices operating across physical, data-link, and network layers. 

- **Layer Operations**: Routers use link-layer and network-layer addresses for each interface, acting only on packets where the link-layer address matches the receiving interface.
- **Address Translation**: Routers change the link-layer address (both source and destination) of packets as they forward them, unlike repeaters or switches.
- **Network Layer Functionality**: By operating at the network layer, routers can make more complex decisions about packet forwarding, including routing based on IP addresses.

These connection devices play critical roles in forming and maintaining the structure and efficiency of Ethernet networks. Hubs, while simple, have given way to more sophisticated switches and routers, which provide enhanced functionality, security, and efficiency in handling network traffic.


* Forouzan, B. A. (2022). *Data Communications and Networking with TCP/IP Protocol Suite* (6th ed.). McGraw Hill LLC.
* [IEEE Standard for Ethernet](https://ieeexplore.ieee.org/document/9844436)
* [Gigabit Ethernet](https://en.wikipedia.org/wiki/Gigabit_Ethernet#Copper)
* [Autonegotiation](https://en.wikipedia.org/wiki/Autonegotiation)
* [Ethernet over twisted pair](https://en.wikipedia.org/wiki/Ethernet_over_twisted_pair)
