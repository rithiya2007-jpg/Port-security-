# Cisco Packet Tracer Switch Port Security Lab

A Cisco Packet Tracer Layer 2 security lab exploring switch port security, MAC address learning, and violation actions.

## Project Overview

This project documents a switch port-security scenario with multiple PCs, including a host labeled as a hacker PC. The topology labels example policies such as sticky MAC learning, manual MAC configuration, maximum devices per port, and violation modes including shutdown, restrict, and protect.

## Features

- Switch port-security concepts
- Sticky and manually configured secure MAC addresses
- Maximum secure MAC address limits
- Violation modes: protect, restrict, and shutdown
- Ping output screenshot showing unsuccessful reachability tests

## Technologies Used

- Cisco Packet Tracer
- Cisco Catalyst switch CLI
- Ethernet
- Layer 2 port security
- MAC address learning

## Project Structure

```text
packet-tracer-port-security-lab/
├── README.md
└── screenshots/
    └── port-security-topology-and-ping-test.jpg
```

## Network Topology Details

The screenshot shows a central access switch connected to several PCs on `192.168.10.0/24`, with example host labels `192.168.10.1` through `192.168.10.5`. Policy callouts identify different port-security approaches. Exact switchport-to-host mappings and the final port-security configuration are not fully visible.

## How to Recreate and Test

1. Add a 2960 switch and several PCs.
2. Connect each PC to a separate access port and assign unique addresses in a common subnet, for example `192.168.10.0/24`.
3. On the switch, enable port security on selected access ports. Configure the maximum number of secure MAC addresses and choose sticky learning or manually configured addresses.
4. Choose a violation action appropriate to the exercise: `protect`, `restrict`, or `shutdown`.
5. Generate traffic, then test what happens when a different device is connected to a protected port.
6. Inspect the switch's port-security state and violation counters.
7. Save the recreated topology as a `.pkt` file.

## Useful Verification Commands

```text
enable
show port-security
show port-security interface fastethernet0/1
show port-security address
show interfaces status

# Illustrative access-port configuration
configure terminal
interface fastethernet0/1
 switchport mode access
 switchport port-security
 switchport port-security maximum 1
 switchport port-security mac-address sticky
 switchport port-security violation shutdown
end
show port-security interface fastethernet0/1
```

## Expected Results

A port should learn or accept only the permitted number of secure MAC addresses. A violation triggers the configured action. The screenshot shows ping requests timing out, but timeouts alone do not prove port security caused the failure; addressing, cabling, or other configuration issues may also cause them.

## Screenshots

![Port Security Topology And Ping Test](screenshots/port-security-topology-and-ping-test.jpg)

## Important Notes

The original `.pkt` file was not provided. This package contains screenshots and documentation only. Commands are examples and have not been tested against the original project. Port-security command support can vary by Packet Tracer device model and software version.

## Portfolio Use

This repository is intended as networking-lab documentation for a student internship portfolio. To present it as a completed practical implementation, recreate and verify the topology in Cisco Packet Tracer and add the resulting `.pkt` file and your own test evidence.
