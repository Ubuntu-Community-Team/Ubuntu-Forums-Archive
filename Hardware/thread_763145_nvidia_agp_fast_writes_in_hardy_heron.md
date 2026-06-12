---
title: "nvidia agp fast writes in hardy heron"
date: 2008-04-22
forum: Hardware
---

### Post by glennric on 2008-04-22
Does anyone know how to enable agp fast writes and side band addressing for nvidia in hardy herron?  The old method of adding 
```
options nvidia NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1

```
to /etc/modprobe.d/nvidia-kernel-nkc doesn't seem to work anymore.  I have tried changing nvidia to nvidia-new or nvidia_new to no avail as well.

---

### Post by glennric on 2008-04-22
For some reason the contents of the file /etc/modprobe.d/nvidia-kernel-nkc are ignored entirely.  I am able to manually modprobe the nvidia module with these options, but how can I make it take effect at startup?

---

### Post by vectorslave on 2008-06-07
Same problem here!
I have try this method but nothing happens. :(

I have Nvdia 6600GT and the latest nvidia drivers by EnvyNG!

analog@analog-desktop:~$ cat /proc/driver/nvidia/agp/status
Status: 	 Enabled
Driver: 	 AGPGART
AGP Rate: 	 8x
Fast Writes: 	 Disabled
SBA: 		 Enabled

---

