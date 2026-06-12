---
title: "Wireless freezing on HP Probook"
date: 2024-09-24
forum: Hardware
---

### Post by nodsec on 2024-09-24
During the data downloading, wireless network is randomly freezing on HP Probook (durig this time is download or upload 0kB/s). After few seconds wireless communication unfreeze and works until next freeze. I spend a lot of time, but didn't found the solution. Any idea, how to solve this problem?


Ubuntu: 24.04.1 LTS (but same problem was on all previous distros)

Wireless adapter:
*-network
       description: Wireless interface
       product: Wireless 8265 / 8275
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0
       version: 78
       serial: ****
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=6.8.0-45-generic firmware=36.ca7b901d.0 8265-36.ucode ip=**** latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:149 memory:b3200000-b3201fff


Wireless adapter hardware:
03:00.0 Network controller [0280]: Intel Corporation Wireless 8265 / 8275 [8086:24fd] (rev 78)
        Subsystem: Intel Corporation Dual Band Wireless-AC 8265 [8086:1010]
        Kernel driver in use: iwlwifi
        Kernel modules: iwlwifi

Thanks a lot for and each help or experience.
Is it somehow possible to solve this problem, or I must buy another notebook?

---

