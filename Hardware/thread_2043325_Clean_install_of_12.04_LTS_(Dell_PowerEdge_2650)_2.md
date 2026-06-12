---
title: "Clean install of 12.04 LTS (Dell PowerEdge 2650) 2004"
date: 2012-08-16
forum: Hardware
---

### Post by Trzone on 2012-08-16
Some information

We are moving from 8.04 LTS to 12.04 LTS on a Dell PowerEdge 2650 server (rack mounted)

Would 12.04 LTS support the hardware RAID controller?
Would we have to load a module or get a specific driver? (this is from 2004 so not sure if dell has any drivers for this controller)

From LSHW

*-storage
          description: RAID bus controller
          product: PowerEdge Expandable RAID Controller 3/Di
          vendor: Dell
          physical id: 8.1
          logical name: scsi0
          capabilities: storage pm bus_master cap_list emulated
          configuration: driver=aacraid latency=32 module=aacraid

Any suggestions / thoughts would be greatly appreciated!

Thank You

---

