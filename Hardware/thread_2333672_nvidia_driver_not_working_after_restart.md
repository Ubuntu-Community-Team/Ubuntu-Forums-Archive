---
title: "nvidia driver not working after restart"
date: 2016-08-12
forum: Hardware
---

### Post by Seyed_Ali_Mousavi on 2016-08-12
Hi,

I'm not an nvidia ubuntu expert. My labmate across the world, rebooted the server and didnt "mount" the nvidia drivers. when I want to do nvidia-smi i get:

```
udo nvidia-smi
modprobe: ERROR: could not insert 'nvidia_304': No such device
NVIDIA: failed to load the NVIDIA kernel module.
[COLOR=#29F914][FONT=&quot]NVIDIA-SMI has failed because it couldn't communicate with NVIDIA driver. Make sure that latest NVIDIA driver is installed and running[/FONT][/COLOR]
``` 

how do I go about solving this?

---

### Post by howefield on 2016-08-12
Thread moved to the "*Hardware*" forum for a better fit.

What is the model of the graphics card ?

```
lspci | grep "VGA"
```

---

### Post by Seyed_Ali_Mousavi on 2016-08-12
```

lspci | grep "VGA"
01:00.0 VGA compatible controller: NVIDIA Corporation GM200 [GeForce GTX TITAN X] (rev a1)
02:00.0 VGA compatible controller: NVIDIA Corporation GM200 [GeForce GTX TITAN X] (rev a1)
03:00.0 VGA compatible controller: NVIDIA Corporation GM200 [GeForce GTX TITAN X] (rev a1)
04:00.0 VGA compatible controller: NVIDIA Corporation GM200 [GeForce GTX TITAN X] (rev a1)

```

---

