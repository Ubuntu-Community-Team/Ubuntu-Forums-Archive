---
title: "NVIDIA nForce Networking Controller after suspend"
date: 2008-11-30
forum: Hardware
---

### Post by StageCraft on 2008-11-30
After a fair bit of digging, I have come to the conclusion that this is a hardware problem. After I suspend my desktop, the network manager says that the network is disconnected, but it works fine after a reboot.

Is there a way to either:
 a) convince the computer that yes, it is connected 
or
 b) run a little script to reset the hardware after it wakes up so that the Network controller will be restarted, but nothing else will.

Note: This was not a problem in 8.04, only now in 8.10 after upgrade.

---

### Post by Nisuspi on 2008-12-01
Same here - using an NVIDIA 790 motherboard and since the upgrade to 8.10 I have no wired network after suspend. Tried WICD as well as Network Manager to get round it. 

I did have the same problem with 8.04 though, but adding a line to the ACPI scripts to tell networking to shut down before suspend sorted it. Doesn't work any more though.

---

