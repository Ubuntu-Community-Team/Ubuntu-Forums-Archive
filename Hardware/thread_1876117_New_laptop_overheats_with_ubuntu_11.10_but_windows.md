---
title: "New laptop overheats with ubuntu 11.10 but windows7 stays cool as ice"
date: 2011-11-05
forum: Hardware
---

### Post by mattasp on 2011-11-05
I have a new laptop, its mayby 8 or 9 months old, with intel cor i3 4gb of ram and so on.
Funny thing is that with windows the fan is mostly off. But with the ubuntu it's always on! When i feel under the laptop with my hands it probably 60 degrees. Sometimes the computer just shuts off from overheating. I dont even need to run anything to make the computer overheat. 

I was told that ubuntu requires less from a computer but it seems quite opposite for me.

---

### Post by diasf on 2011-11-05
cpufreqd
(seems like your cpu is locked on max frequency, and probably with cooler problems as well - on the control systems).

Ubuntu works fine. But on some system it requires some extensive tweaking for fan and cpufrequency controls.

---

### Post by feelizia on 2011-11-27
Hello,

I have the same problem.

I started to use Ubuntu 11.10 two days ago and now my notebook is overheating all the time. I did not have any problem with version 10.10 before. 

What can I do to fix the problem??

Best regards

feelizia

---

### Post by Mark Phelps on 2011-11-29
Sorry folks ... but this is an ongoing "bug" with the new kernel version distributed with Ubuntu 11.10 ... and there is no current fix for it.

---

### Post by senchan on 2011-12-20
:(

IS there anyway of downgrading the kernel or sth? Or do I really have to reinstall my Ubuntu with an older version than 11.10?

---

### Post by xyzzyman on 2011-12-20
The ASPM fix has been applied to the latest rc6 kernel build in precise. You can install that kernel on oneiric. If you're on 64-bit here's the downloads:


[http://launchpadlibrarian.net/87895001/linux-headers-3.2.0-6_3.2.0-6.12_all.deb](http://launchpadlibrarian.net/87895001/linux-headers-3.2.0-6_3.2.0-6.12_all.deb)
[http://launchpadlibrarian.net/87876765/linux-headers-3.2.0-6-generic_3.2.0-6.12_amd64.deb](http://launchpadlibrarian.net/87876765/linux-headers-3.2.0-6-generic_3.2.0-6.12_amd64.deb)
[http://launchpadlibrarian.net/87876762/linux-image-3.2.0-6-generic_3.2.0-6.12_amd64.deb](http://launchpadlibrarian.net/87876762/linux-image-3.2.0-6-generic_3.2.0-6.12_amd64.deb)

Install in that order also. If you have a problem just choose 'previous' at the grub prompt and uninstall these.

---

### Post by Moriarty123456 on 2011-12-21
Just FYI, I have/had a similar problem with my Lenovo B570 (i5 sandybridge processor, dualboot 11.10 and win7). The problem was not so much overheating but constant fan noise. 

It now seems to run a little better after I did the following:

1) install  lm-sensors. In a terminal (to open a terminal type ctrl-alt t): 
```
apt-get install lm-sensors
```2) then run
```
su sensors-detect
```Follow the simple instructions (mostly typing "YES") then the output spat out some geeky codes like:
> driver `i2c-i801' for device 0000:00:1f.3: Intel Cougar Point (PCH)
Module i2c-i801 loaded successfully.
Module i2c-dev loaded successfully.
Driver `coretemp':
* Chip `Intel digital thermal sensor' (confidence: 9)
It then said it was automatically going to add the below line to /etc/modules, was that OK?:

> # Chip drivers
coretemp Sure! Says I. Then in the terminal, to complete, run:
```
sudo service module-init-tools start
```Now, the fans are on less, at less speed (but they are still mostly on..) and the battery life seems to have improved a bit. Also I am able to run 'sensors' from the terminal and get more info than before.
I now get: 
> david@david-Lenovo-B570:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +52.0°C  (crit = +98.0°C)
temp2:        +35.0°C  (crit = +126.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +53.0°C  (high = +86.0°C, crit = +100.0°C)
Core 0:         +53.0°C  (high = +86.0°C, crit = +100.0°C)
Core 1:         +50.0°C  (high = +86.0°C, crit = +100.0°C)

Whereas before I didn't get the coretemp-isa-000 bit. 

Hope that helps somebody.

---

### Post by nshiell on 2011-12-21
Same hot behaviour on a macbook 2,1

---

### Post by Jay Car on 2011-12-21
> **nshiell said:**
> Same hot behaviour on a macbook 2,1

I haven't had any overheating problems with my laptops, but I'm wondering if this might help fix it for others. [Jupiter]("http://www.webupd8.org/2010/07/jupiter-ubuntu-ppa-hardware-and-power.html")

---

### Post by dgakkhar on 2012-01-09
> **xyzzyman said:**
> The ASPM fix has been applied to the latest rc6 kernel build in precise. You can install that kernel on oneiric. If you're on 64-bit here's the downloads:


[http://launchpadlibrarian.net/87895001/linux-headers-3.2.0-6_3.2.0-6.12_all.deb](http://launchpadlibrarian.net/87895001/linux-headers-3.2.0-6_3.2.0-6.12_all.deb)
[http://launchpadlibrarian.net/87876765/linux-headers-3.2.0-6-generic_3.2.0-6.12_amd64.deb](http://launchpadlibrarian.net/87876765/linux-headers-3.2.0-6-generic_3.2.0-6.12_amd64.deb)
[http://launchpadlibrarian.net/87876762/linux-image-3.2.0-6-generic_3.2.0-6.12_amd64.deb](http://launchpadlibrarian.net/87876762/linux-image-3.2.0-6-generic_3.2.0-6.12_amd64.deb)

Install in that order also. If you have a problem just choose 'previous' at the grub prompt and uninstall these.

I installed the kernel. The condition is way way much better than before. It does n't over heat now. Thanks a lot for it. But I think that it's using more power than a windows system  or the laptop fan is on at fast speed always. anyways thank a ton.

---

### Post by aeronutt on 2012-01-09
These kernel options increased my battery life by 2.5X, so will reduce heat also. Not sure if they'll work with those latest RC kernel releases, but maybe worth a try.

[http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1)

---

### Post by manishlogan on 2012-02-21
I face the same problem with Sony Vaio laptop, ci3 processor. Till the time I was using Ubuntu 11.04 or older versions, things were great, but as soon as I upgraded to 11.10, the heating problem started.

---

### Post by Morozov on 2012-02-21
Ihave tryed New Kernel with 11.10 64bit yesterday on Dell Studio xps 1340 and got much better esponce from computer, video card stable, less heat and longer battery life. Ive' tryed new 12.04 as well and that wouldbe be OS for my laptop (solved try and error video card problem)

---

### Post by Kissell on 2012-02-27
> **xyzzyman said:**
> 
[http://launchpadlibrarian.net/87895001/linux-headers-3.2.0-6_3.2.0-6.12_all.deb](http://launchpadlibrarian.net/87895001/linux-headers-3.2.0-6_3.2.0-6.12_all.deb)
[http://launchpadlibrarian.net/87876765/linux-headers-3.2.0-6-generic_3.2.0-6.12_amd64.deb](http://launchpadlibrarian.net/87876765/linux-headers-3.2.0-6-generic_3.2.0-6.12_amd64.deb)
[http://launchpadlibrarian.net/87876762/linux-image-3.2.0-6-generic_3.2.0-6.12_amd64.deb](http://launchpadlibrarian.net/87876762/linux-image-3.2.0-6-generic_3.2.0-6.12_amd64.deb)


I followed these instructions to upgrade the kernel on my Acer Aspire 5536-C3 that I bought in Japan.
uname -a
```

Linux Acer-Aspire 3.2.0-6-generic #12-Ubuntu SMP Mon Dec 19 03:37:01 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

```

Before the upgrade the CPU was probably at 2100000 most of the time, now it often is at 1050000 but can still be at 2100000 with the computer idle.

cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_cur_freq
```

2100000

```

These steps did upgrade my kernel and I think the CPU is not working so hard now for no reason, however, the fan is still on constantly and it is running very hot, I expect it to automatically shutdown any minute now.

I read a post that you could turn off the extra VGA output port on the laptop that isn't ever used...  and that would reduce heat by 20C.  However, the instructions didn't work for me, probably because mine is an ATI Radeon 3200HD, which is slightly different from the instructions here.
[http://cisight.com/switch-off-ati-vga-in-dual-vga-with-intel-on-ubuntu-to-solve-overheat-problem/]("http://cisight.com/switch-off-ati-vga-in-dual-vga-with-intel-on-ubuntu-to-solve-overheat-problem/")

So I'm still not fixed?  But, on the plus side, my kernel is newer!  :)

BTW: The only way I've found to solve the heat issue was to load an older version of Ubuntu...  Using Lubuntu 11.04 does not have the over heating issue... so it must be something in the 11.10 kernel or video drivers...  unfortunately, it looks like the kernel in 12.04 isn't going to fix this issue for me that has been going on for many many months now.

---

