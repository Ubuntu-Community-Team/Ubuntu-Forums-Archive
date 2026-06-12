---
title: "Severe NVME Issue with Ubuntu 16.04 and Samsung 960 Pro M2 SSD"
date: 2016-12-24
forum: Hardware
---

### Post by roots on 2016-12-24
Hi All & Merry X-Mas,

I'm having severe troubles with my new Samsung Pro 960 M2  SSD.
The drive is sitting in a M2-PCIe adapter on a PCIe16x slot of my Gigabyte GA-Z77X-UD3H mobo and is working completely fine under Windows 7.

With Ubuntu 16.04 however, I am not getting it to work properly. Here's what happens:

-The drive is recognised fine after boot in first place, shows with "lspci" and "nvme list" will give me correct output
-The drive will go "missing" after a duration of approx. 5 to 1000 seconds for no obvious reason, here's what dmesg | grep nvme gives:

[   37.805783] nvme 0000:01:00.0: Failed status: 0xffffffff, reset controller.
[   37.825887] nvme 0000:01:00.0: Refused to change power state, currently in D3
[   37.825934] nvme nvme0: Removing after probe failure status: -19
[   37.825941] nvme0n1: detected capacity change from 1024209543168 to 0

-After this occurs, the drives is _sometimes_ also missing from lspci
-This will happen both if the drive is idle and also if I managed to mount it and are running e.g. benchmarks on it
-The duration after which the drive is going offline seems to be completely random

I've tried with Kernels 4.4.0-53, 4.4.0-58, 4.9.0 - no difference.

The drive itself appears to be OK, as I've been running it for an hour or so under Windows7 without troubles. Any suggestion where I should be looking into?!


THANKS!
r.

---

### Post by oldfred on 2016-12-24
Is this your issue?
 Asus/Samsung problem with every NVME SSD and G752! 
[https://ubuntuforums.org/showthread.php?t=2307273&p=13584551#post13584551](https://ubuntuforums.org/showthread.php?t=2307273&p=13584551#post13584551)
[http://askubuntu.com/questions/861854/nvme-disk-configured-in-raid0-unable-to-install-ubuntu-16-04](http://askubuntu.com/questions/861854/nvme-disk-configured-in-raid0-unable-to-install-ubuntu-16-04)

---

### Post by roots on 2016-12-26
Thanks, but not exactly. However, it seems to be a BIOS issue, the drive is not recognised by the BIOS in any way. Not being able to boot from it is my least concern atm, but there are other spooky (and seemingly uncorrelated) effects like:

-If I change from default BIOS settings to overclocked ones, the NVME drive will not be seen by the OS anymore
-If my HDD drive is going to sleep (via hdparm), the NVME drive will get disconnected as in my original post.

Both effects are reproducible. 

Aside from that, I've even managed to install 16.04 onto drive drive and are running fine with it, as long as my HDD drive is spinning and my BIOS is at default settings :-)
There are no later BIOS versions than the one I'm using, but I know of the possibility to insert later BIOS's NVME drivers and baking a custom BIOS. However, I will upgrade my mainboard within the next weeks anyway, so I will try without in the meantime.

---

### Post by tmus on 2016-12-28
I can't tell you how to solve this, but I'm experiencing the same issue on my laptop here. After a recent BIOS upgrade I went 6 full days with no indication of an issue, but tonight it's back with a vengance. 4 times have I lost my work and had to restart tonight.

The problem is unpredictable here - I have no way of knowing when it might happen, but when it happens, it seems like there's a real good chance it'll do it again within a few minutes of rebooting.

I have not yet been able to reproduce, so im very interested in hearing which hdparm command you use to trigger this issue?

/Thomas

---

### Post by roots on 2016-12-29
Hi,
what mainboard is your laptop using, btw. what's the exact laptop model? For the first, please give us the output of
```
sudo dmidecode -t2
```

Please also give us the output of 
```
sudo dmidecode -t0
```

I've now switched to a different mainboard and CPU and still see this kind of issue - however, it's a Gigabyte mainboard again...

r.

---

### Post by WinEunuchs2Unix on 2017-10-11
About to install 960 Pro and am curious if you have resolve this issue?

My plan is to install latest Firmware 2.2 under Windows. There is also a Windows driver which of course won't work under Linux. Hopefully the firmware is "sticky" under both Win and Linux. I know it's been almost 10 months but hopefully there was a solution.

---

### Post by oldfred on 2017-10-11
I could not get Linux version to work.
Windows version is in consumer, Linux version in Enterprise.

 [http://www.samsung.com/semiconductor/minisite/ssd/downloads/software/Samsung_Magician_DC_Linux_64bit.zip](http://www.samsung.com/semiconductor/minisite/ssd/downloads/software/Samsung_Magician_DC_Linux_64bit.zip)
[http://askubuntu.com/questions/808828/how-to-install-samsung-magician](http://askubuntu.com/questions/808828/how-to-install-samsung-magician)

---

### Post by roots on 2017-11-22
Hi,

sorry guys for the late reply.

So far I've found out that the problem may be an intrinsic issue with the drive itself or in combination with certain mainboards (Gigabyte, for example), please see [https://tinkertry.com/supermicro-superserver-bios-change-can-cause-960-pro-and-evo-to-hide-heres-the-fix](https://tinkertry.com/supermicro-superserver-bios-change-can-cause-960-pro-and-evo-to-hide-heres-the-fix)

My status with the issue is as follows: When starting my PC, occasionally (maybe 2 out of 10 times) the drive will not be detected during POST. As it is my system drive, I won't be able to boot. Resetting btw. cold-starting my PC will, in most cases, make POST detect the drive, sometimes only with the 3rd attempt. It appears to be correlated to the time span between switching on the PSU mains switch and the power-on button - it will work most times when this time span is short (<5s). This also means in my case, after soft-shutting down the system without successively switching PSU mains power off, in most cases the SSD won't be found by POST when soft-powering on after some minutes or hours. Sounds a little like indicated in the above link. 
However, after successfully booting into Ubuntu, I've only had 2 freezes within the last 6 months, both occured when I was absent and the screen was locked. Yet I can't say with certainty that this was caused by the drive gone missing.
I've tried the most recent Samsung firmware, but that did not solve the problem. I've tried updating the BIOS, but would not be able to boot Ubuntu due to some wrong default BIOS settings and I did not have the time yet to debug this, so I reverted back to the old BIOS.

Indicative of this issue is the high SMART unsafe_shutdowns count, which is >1200 here. However, SMART does not show any other errors for the drive.

Maybe this is of some help for you ... did you get the issue sorted?


Cheers,
r.

---

### Post by oldfred on 2017-11-22
Do you have a fast boot setting in UEFI?
If so turn that off.

UEFI fast boot does speed boot. But it is assuming no system changes and immediately starts boot process from hard drive. Normally it takes a few seconds to scan what hardware you have and then writes that info to drive for system to use.
Back in BIOS days, memory check and BIOS took minutes. UEFI is faster and then fast boot even faster still.
But if hard drive is not ready, especially external drives, or slower HDD, but can be any drive, then system fails to boot.

---

### Post by roots on 2017-11-22
Thanks, but I have fast boot disabled and the other stuff set to legacy by default. I'm admitting I'm a BIOS guy... ;-) I've been toying with all relevant BIOS settings and then some, but none of the changes helped with the issue.

---

