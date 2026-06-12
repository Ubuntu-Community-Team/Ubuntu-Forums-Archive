---
title: "Compaq CQ60-210TU CPU NOT Throttling"
date: 2009-03-06
forum: Hardware
---

### Post by Moustacha on 2009-03-06
Just bought myself one of these. Everything is working fine (wireless too) but it won't throttle the CPU. When I load the applet onto the task bar it says "...your machine may be misconfigured or not have hardware support for CPU frequency scaling". Now it's brand new so it must be a configuration issue. Can anyone point me in the right direction please?

It's a dual-core celeron 1.66GHz on a "series 4" intel chipset


Edit: Well the solution is loading p4-clockmod as acpi-cpufreq doesn't seem to work with it, or speedstep-centrino. modprobing p4-clockmod in then restarting the gnome-applet seems to have done the trick

---

### Post by afeasfaerw23231233 on 2009-03-16
Hi, I have exactly the same issue as you! I am having a T1600 celeron dual-core 1.66Ghz too. It's running at stock frequency all the time and the notebook is hot and noisy. Would you please tell me how to enable scaling by modprobing p4-clockmod? Thanks!

EDIT:I did sudo modprobe p4-clockmod in terminal and scaling is working now. Thanks for your thread.

---

### Post by Moustacha on 2009-03-16
open a terminal and run this command.

```
$ sudo modprobe p4-clockmod
```
that loads the p4-clockmod module. To make sure it will always load at start up you need to put it into /etc/modules

```
$ sudo vim /etc/modules
```
then put 'p4-clockmod' at the bottom, without the '

Once you've done that, remove the cpu monitoring applet from your gnome panel if it's on there, then add it again and it should show the cpu being ~200MHz.

For some reason setting the applet to run with super user privelages doesn't let you change the governer on-demand, it still asks you for the sudo password.

---

### Post by afeasfaerw23231233 on 2009-03-16
Bad news! I searched the forum and found out that p4-clockmod actually won't save power usage. 
[http://ubuntuforums.org/showthread.php?t=309403](http://ubuntuforums.org/showthread.php?t=309403)

```

p4-clockmod: Warning: Pentium M detected. The speedstep_centrino module offers voltage scaling in addition of frequency scaling. You should use that instead of p4-clockmod, if possible.
```
It's a 'throttling" feature to lower the FSB frequency while the cpu is overheat. The true power saving speedstep lowers the voltage and the multiplier. 
p4-clockmod won't increase the battery runtime. 

It can be confirm by running the command 
cat /proc/acpi/battery/BAT0/state

It may lower the fan speed as the cpu is a bit cooler and may save 1 watt. But no significant actual use for saving power consumption

p.s.
The power consumption of my notebook is always higher then 24W (11.1V x 2.2A) even it is idle (wifi off, min brightness, speakers mute, etc). I guess EIST not enable is the cause. I cannot get speedstep work in XP either. 
I don't know if it's the BIOS or chipsets or OS problem. 
My notebook is with the darn SiS 671MX chipsets.

What's your spec?

---

### Post by Moustacha on 2009-03-16
The intel website says the CPU supports EIST...if it's the mobile celeron. I *hope* they put the mobile version in my laptop =\
[http://processorfinder.intel.com/Details.aspx?sSpec=SLB6J](http://processorfinder.intel.com/Details.aspx?sSpec=SLB6J)

I'm gonna have to google more and see if i can find a solution

There also seems to be this bug
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/332846](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/332846)
I'm gonna give another distro a go and see if it solves that

---

### Post by afeasfaerw23231233 on 2009-03-16
I am sure my cpu is a Mobile Celeron Dual-core as I can see it's a small socket P 479-pin cpu (the cpu just lie beside the ram slot) with the string "166 x 10 =1.66Ghz 1MB cache T1600 etc. lshw and /proc/cpuinfo also match the T1600 specifications of T1600 on the intel processor finder page. If it's a desktop cpu it will be so huge to fit inside the notebook (LGA 775). The  I bet yours is Mobile Celeron Dual-core t1600 too. 
The BIOS has no available setting beside boot order. Speedstep/EIST doesn't work on windows xp too.

I doubt if it is a BIOS problem. 
In the firmware section of "sudo lshw" 
```
     *-firmware
          description: BIOS
          vendor: OEM
          physical id: 0
          version: 1.13 (07/05/2008)
          size: 107KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect
 edd int13floppynec int13floppy360 int13floppy1200 int13floppy720 int13floppy288
0 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification

```
There's no speedstep or EIST listed on the capabilities line. 
I am searching the web to see whether the firmware section of "sudo firmware" from a system with a speedstep capable cpu has an extra item listed on the capabilities line.

---

### Post by afeasfaerw23231233 on 2009-03-16
I find some information.
According to this page
[http://blog.incase.de/index.php/cpu-feature-flags-and-their-meanings/](http://blog.incase.de/index.php/cpu-feature-flags-and-their-meanings/)
EST/EIST is stand for speedstep. If it doesn't show up in /proc/cpuinfo then it may be a BIOS problem. Have a look at this bug report [https://bugzilla.redhat.com/show_bug.cgi?id=221728](https://bugzilla.redhat.com/show_bug.cgi?id=221728)

That should explain why I can't get frequency scaling work on windows xp too. 
huh, it is running hot and battery life time is short! 

I googled the web for "cat /proc/acpi/battery/BAT0/state" and most notebooks with the same spec as mine have a power consumption of 15W - 18W (A x V). But mine is drawing more than 24W even it is doing nothing and everything is at minimal! I have tried laptop-mode. Doesn't make big difference.

Wish that I can modify BIOS settings by a software!

---

### Post by Moustacha on 2009-03-17
If it is a BIOS bug I don't have much hope of trying to fix it then. The level of secrecy in laptop BIOS' is insane.

---

### Post by afeasfaerw23231233 on 2009-03-17
Unluckily the customer support site doesn't provide any BIOS for me to download. I sent an email to request for a BIOS (either the old one or an updated version) two weeks ago. Never get any reply. Worst customer support ever. 
It is the crappiest BIOS I have ever seen. The only avilable settings are date/time and boot orders. Long time ago I borrowed a PIII notebook from the library and the setting in its BIOS was much more detail.

---

