---
title: "NVIDIA: Fast Writes"
date: 2008-09-01
forum: Hardware
---

### Post by nrs on 2008-09-01
The problem is fast writes seem to be disabled by default.
```
cat /proc/driver/nvidia/agp/status 
Status:          Enabled
Driver:          AGPGART
AGP Rate:        8x
Fast Writes:     Disabled
SBA:             Enabled
```
I've tried adding  NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1 to /etc/modprobe.d/nvidia-kernel-nkc the file now looks like
```
alias char-major-195* nvidia options nvidia NVreg_DeviceFileUID=0 NVreg_DeviceFileGID=44 NVreg_DeviceFileMode=0660 NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1
```
No joy. My card and motherboard support this, I had it working under Gentoo, and if I load the driver manually with modprobe -i & the options listed above, it works. I don't won't to have to do that every restart though.

Solutions?

---

