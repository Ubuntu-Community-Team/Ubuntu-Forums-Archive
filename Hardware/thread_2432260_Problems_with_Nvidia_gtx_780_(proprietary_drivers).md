---
title: "Problems with Nvidia gtx 780 (proprietary drivers)"
date: 2019-11-29
forum: Hardware
---

### Post by vagna on 2019-11-29
Hello, I'm trying to get a gtx 780 to work on my ubuntu installation. 
Specifically it's this model from asus [https://www.asus.com/Graphics-Cards/GTX780DC23GD5/](https://www.asus.com/Graphics-Cards/GTX780DC23GD5/)

At first I had the system running on the integrated intel gpu. 
Then I installed the nvidia proprietary drivers (newest ones, nvidia-driver-440) and put in the graphics card. When I booted, after the the kubuntu logo I see a black screen with a blinking underscore. 
Trying different drivers gets me the same result, the older drivers (340,390) giving me additional blue tears on the screen and no option to switch to tty2 with Ctrl-Alt-F2.
Created /etc/modeprobe.d/blacklist-nvidia-nouveau.conf
containing
```

blacklist nouveau
options nouveau modeset=0

```
No change.
Tried adding nomodeset in grub, no change.

After changing a line in /etc/default/grub from
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
to
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nvidia-drm.modeset=1"
```
I got X running again but it doesn't use the driver and the resolution is 640x480.

Currently I'm having the nvidia-driver-418 installed.
If I install older drivers (390 for example) I get the black screen with blinking underscore and blue tears, installing newer drivers get X to run but it doesn't load the drivers.

I've searched quite a lot and I'm a bit lost. Hopefully someone can help me.

---

### Post by him610 on 2019-11-29
>  I installed the nvidia proprietary drivers
Where did you get the nvidia drivers from? 
I have a similar card, a GTX 760, using nvidia driver 430.50 that was downloaded from the Ubuntu repositories. 
Sometimes it is better to let the nouveau driver load first then download and install the nvidia drivers from Additional Software.

---

### Post by vagna on 2019-11-30
The ppa repository.

Thing is, even if I deinstall the drivers, I get a black screen with a blinking underscore so the card doesn't even want to work properly with nouveau it seems.

Dmesg gives me 
> 
[  416.096724] NVRM: GPU at PCI:0000:01:00: GPU-462c5715-f9c5-3eed-56ad-35fdd066205f
[  416.096726] NVRM: Xid (PCI:0000:01:00): 62, pid=2763, 0c83(1870) 00000000 00000000
[  428.099213] NVRM: GPU 0000:01:00.0: RmInitAdapter failed! (0x26:0x1a:1227)
[  428.099283] NVRM: GPU 0000:01:00.0: rm_init_adapter failed, device minor number 0

Maybe the card is broken but I don't know how to verify that.

---

