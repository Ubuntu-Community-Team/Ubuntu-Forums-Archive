---
title: "Karmic Nvidia 173 Driver Fast Writes"
date: 2010-03-07
forum: Hardware
---

### Post by kempy1000 on 2010-03-07
Hi,

I am trying to enable fast writes on my nvidia Fx5200 under ubuntu 9.10.

cat /proc/driver/nvidia/agp/status
```

Status:          Enabled
Driver:          AGPGART
AGP Rate:        8x
Fast Writes:     Disabled
SBA:             Enabled

```

cat /proc/driver/nvidia/agp/host-bridge
```

Host Bridge:     PCI device 1106:0204
Fast Writes:     Supported
SBA:             Supported
AGP Rates:       8x 4x
Registers:       0x1f000a1b:0x00000b02

```

cat /proc/driver/nvidia/agp/card
```

Fast Writes:     Supported
SBA:             Supported
AGP Rates:       8x 4x
Registers:       0x1f000e1b:0x1f000302

```

So according to all these Fast writes is possible! But is disabled.
There is no bios option to enable Fast Writes.
And most guides say to edit /etc/modprobe.d/nvidia-kernel-nkc
but this file and folder is non-existent in 9.10.

Thanks
Chris

---

### Post by pyrobutters on 2010-05-08
I think this will help. It appears that in Karmic, you must create the file, to enable fastwrites. This worked for my nvidia driver 96. This should work for other Nvidia drivers as well.


sudo gedit /etc/modprobe.d/nvidia

then add this to the newly made "nvidia" file. 

alias char-major-195* nvidia
options nvidia NVreg_EnableAGPFW=1 


Hope that helps

---

### Post by pyrobutters on 2010-05-08
and I forgot, and reboot the system after you applied the settings.
 cheers.:p

---

