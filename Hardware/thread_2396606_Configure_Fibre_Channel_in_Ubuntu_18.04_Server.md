---
title: "Configure Fibre Channel in Ubuntu 18.04 Server"
date: 2018-07-18
forum: Hardware
---

### Post by esmarcat on 2018-07-18
Hello,


I need help configuring a Fujitsu Storage Eternus DX80 S2 to an Ubuntu 18.04 server fiber adapter (Fibre Channel: Emulex LPe12002 Corporation Saturn-X: LightPulse Fibre Channel Host Adapter (rev 03)).


Is it possible find Emulex LPe12002 drivers for Ubuntu 18.04 server?


*port_state = "Linkdown"*


What should I do?


Thanks for your help,


More information:


02:00.1 Fibre Channel: Emulex Corporation Saturn-X: LightPulse Fibre Channel Host Adapter (rev 03)
        Subsystem: Emulex Corporation Saturn-X: LightPulse Fibre Channel Host Adapter
        Flags: bus master, fast devsel, latency 0, IRQ 85, NUMA node 0
        Memory at fbb88000 (64-bit, non-prefetchable) [size=4K]
        Memory at fbb80000 (64-bit, non-prefetchable) [size=16K]
        I/O ports at d000 [size=256]
        Expansion ROM at fbb00000 [disabled] [size=256K]
        Capabilities: [58] Power Management version 3
        Capabilities: [60] MSI: Enable- Count=1/16 Maskable+ 64bit+
        Capabilities: [78] MSI-X: Enable+ Count=32 Masked-
        Capabilities: [84] Vital Product Data
        Capabilities: [94] Express Endpoint, MSI 00
        Capabilities: [100] Advanced Error Reporting
        Capabilities: [12c] Power Budgeting <?>
        Kernel driver in use: lpfc
        Kernel modules: lpfc




**Class = "fc_host"**


  Class Device = "host7"
  Class Device path = "/sys/devices/pci0000:00/0000:00:02.0/0000:02:00.0/host7/fc_host/host7"
    active_fc4s         = "0x00 0x00 0x01 0x00 0x00 0x00 0x00 0x01 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 "
    dev_loss_tmo        = "30"
    fabric_name         = "0x0"
    issue_lip           = <store method only>
    max_npiv_vports     = "255"
    maxframe_size       = "2048 bytes"
    node_name           = "0x20000090fa552810"
    npiv_vports_inuse   = "0"
    port_id             = "0x000000"
    port_name           = "0x10000090fa552810"
**    port_state          = "Linkdown"**
    port_type           = "Unknown"
    speed               = "unknown"
    supported_classes   = "Class 3"
    supported_fc4s      = "0x00 0x00 0x01 0x00 0x00 0x00 0x00 0x01 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 "
    supported_speeds    = "2 Gbit, 4 Gbit, 8 Gbit"
    symbolic_name       = "Emulex LPe12002 FV2.01A10 DV12.0.0.0. HN:eida. OS:Linux
"
    tgtid_bind_type     = "wwpn (World Wide Port Name)"
    uevent              = 
    vport_create        = <store method only>
    vport_delete        = <store method only>


    Device = "host7"
    Device path = "/sys/devices/pci0000:00/0000:00:02.0/0000:02:00.0/host7"
      uevent              = "DEVTYPE=scsi_host"




  Class Device = "host8"
  Class Device path = "/sys/devices/pci0000:00/0000:00:02.0/0000:02:00.1/host8/fc_host/host8"
    active_fc4s         = "0x00 0x00 0x01 0x00 0x00 0x00 0x00 0x01 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 "
    dev_loss_tmo        = "30"
    fabric_name         = "0x0"
    issue_lip           = <store method only>
    max_npiv_vports     = "255"
    maxframe_size       = "2048 bytes"
    node_name           = "0x20000090fa552811"
    npiv_vports_inuse   = "0"
    port_id             = "0x000000"
    port_name           = "0x10000090fa552811"
    port_state          = "Linkdown"
    port_type           = "Unknown"
    speed               = "unknown"
    supported_classes   = "Class 3"
    supported_fc4s      = "0x00 0x00 0x01 0x00 0x00 0x00 0x00 0x01 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 "
    supported_speeds    = "2 Gbit, 4 Gbit, 8 Gbit"
    symbolic_name       = "Emulex LPe12002 FV2.01A10 DV12.0.0.0. HN:eida. OS:Linux
"
    tgtid_bind_type     = "wwpn (World Wide Port Name)"
    uevent              = 
    vport_create        = <store method only>
    vport_delete        = <store method only>


    Device = "host8"
    Device path = "/sys/devices/pci0000:00/0000:00:02.0/0000:02:00.1/host8"
      uevent              = "DEVTYPE=scsi_host"

---

