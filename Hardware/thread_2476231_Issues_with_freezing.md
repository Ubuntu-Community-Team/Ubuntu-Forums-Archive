---
title: "Issues with freezing"
date: 2022-06-20
forum: Hardware
---

### Post by kyg203 on 2022-06-20
Hey, 

I'm not sure if I'm able to get logs, since my system freezes within a minute or two, but I am 100% open to trying to get the logs if you guys have any ideas on how?

Not really much else to it, the device turns on, gets past the boot screen, and then after a few minutes the whole thing just freezes and doesn't come back to life. I've waited 3/4 hours and even overnight a few times and it wouldn't do anything. I'm on the latest Ubuntu 18.04 LTS release, I have an Nvidia 940MX paired with an Intel Core i7 (I think 6800) with 12GB RAM and I think 4/6 GB vRAM and a 500 GB HDD. It's a HP Pavilion 15 laptop. 

Half the time I try to turn it on and there's nothing on the screen whatsoever, the power button light stays on and the keyboard backlight stays on, but that's it. I have zero clue if I have any video drivers for the Nvidia 940MX installed, but it does have some sort of Nvidia X Settings.

---

### Post by gdesilva on 2022-06-21
When exactly does it freeze? Are you able to get to the login screen? or does it happen after logging in?

All log files are kept under /var/logs directory - so one option is to use a LiveUSB to boot the system and mount the HDD and then check out the logs. The most important ones are kern.log and syslog 

As mentioned, knowing exactly where the system freezes is very useful before going any further.

---

### Post by TheFu on 2022-06-21
There are 2 types of drivers for nvidia devices in Ubuntu.
a) proprietary nvidia
b) F/LOSS Nouveau 

Figure out which is being used and try the others.  

**lsmod** will show a list of drivers. There is also the X.log file in the logs directory (see above).  That will get you to know which driver is being used.
In /etc/modprobe.d/  are files with specific driver options and some blacklists.  When the proprietary nvidia drivers are installed, I suspect they blacklist the Nouveau driver in there.

On my system with an Nvidia 1030 : 
```
$ lsmod |grep nv
znvpair                81920  2 zfs,zcommon
spl                   122880  5 zfs,icp,znvpair,zcommon,zavl
nvidia_uvm           1003520  0
nvidia_drm             57344  4
nvidia_modeset       1200128  9 nvidia_drm
nvidia              35336192  525 nvidia_uvm,nvidia_modeset
drm_kms_helper        188416  1 nvidia_drm
drm                   491520  8 drm_kms_helper,nvidia,nvidia_drm

```

Using a Try Ubuntu flash drive is also a good way to see if the Nouveau drivers will work, since proprietary drivers shouldn't be available.  If the Try Ubuntu environment has issues, I'd lean towards bad hardware.  GPUs fail sometimes, but sometimes new releases of an OS will have driver issues with old hardware, so I'd also try a few different Linux distros with "Live" boot environments.  Debian, MXLinux, Mint, Fedora, OpenSuSE ... and see if any of those work fine before assuming the hardware is bad.

---

