---
title: "cpu fan never runs since kernel 2.6.17-10"
date: 2007-02-18
forum: Hardware &amp; Laptops
---

### Post by mjrclark on 2007-02-18
COmputer shuts down due to cpu overheating.

Problem described and discussed (however, they seem to be talking about changing the kernel code itself) here- [http://www.mail-archive.com/linux-acpi@vger.kernel.org/msg04204.html]("http://www.mail-archive.com/linux-acpi@vger.kernel.org/msg04204.html")

My emachines 370 machine ran Edgy final fine until the automatic kernel upgrade to 2.6.17-10-server from 2.6.15-27-server. I also installed the generic kernel 2.6.17-11-generic as this computer is now used for desktop use too. (Installed dapper-server, installed kubuntu-desktop or similar, then upgraded to edgy, no errors there).

When apt upgraded the kernel automatically, the fan no longer spun after the grub loading screen using the newer kernels, and the pc rightly shutdown on cpu intensive tasks, however if the older ones are selected from grub, the machine works properly. (But I cannot install fiesty as the installation that uses the new kernels and hangs with cpu overheat)

I have tried adding "pci=noacpi" to the line with the kernel on it in grub, but the fan still does not run. Is acpi=off the correct command? However, that would not help with new installations.
cpuinfo;
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 1
model name      : Intel(R) Celeron(R) CPU 1.80GHz
stepping        : 3
cpu MHz         : 1794.259
cache size      : 128 KB

odd result, no idea what it means; (under 2.6.15-27-server)
matthew@linmat2:/$ cat /proc/acpi/thermal_zone/*/*
<setting not supported>
cooling mode:   passive
<polling disabled>
state:                   passive
temperature:             -270 C
critical (S5):           -264 C
passive:                 -273 C: tc1=0 tc2=0 tsp=600 devices=0xcfceef40
active[0]:               -267 C: devices=0xcfceec00

---

### Post by mjrclark on 2007-02-21
The motherboard is a Trigem [ "Imperial GL"]("http://www.emachine-upgraders.info/dir1/motherboards/socket478/imperial.shtml")

---

### Post by raffytaffy on 2007-02-22
similar problem with sony vaio vgn-fs660/w 

ubuntu 6.10
custom kernel 2.6.20.1

box shuts off during cpu intensive tasks.

for now i have mounted a car amplifier fan under my desk / drilled some air holes and run it non stop @ bottom of laptop. this has solved issue for now. 

here is output without fan

raf@Equinox:~$ cat /proc/acpi/thermal_zone/*/*
<setting not supported>
cooling mode:   passive
<polling disabled>
state:                   ok
temperature:             85 C
critical (S5):           105 C
passive:                 95 C: tc1=1 tc2=5 tsp=10 devices=0xdfae6e

with fan going

raf@Equinox:~$ cat /proc/acpi/thermal_zone/*/*
<setting not supported>
cooling mode:   passive
<polling disabled>
state:                   ok
temperature:             55-65~ C
critical (S5):           105 C
passive:                 95 C: tc1=1 tc2=5 tsp=10 devices=0xdfae6e

---

### Post by mjrclark on 2007-02-22
That sounds an effective if not drastic way of dealing with it.  I must admit I was hoping to deal with it in software (or by moving the molex for the fan- but I do not know where to). I guess a software solution without kernel hacking would be to use an older kernel- 

[http://help.ubuntu.com/community/Kernel]("http://help.ubuntu.com/community/Kernel") suggests that this is possible, but I was unable to find any instructions for carrying it out.

I have achieved this under edgy by upgrading from dapper and continuing to use the dapper default kernel, but my attempts to transplant this kernel to a feisty herd 4installation on another partition have bean unsuccessful.

---

### Post by neubert500 on 2007-04-08
I really hope someone can help with this issue as it is identical to the problem we are experiencing on my wife's Emachines W2646. We currently have the side cover off and a fan blowing into the box. It works but this is a redneck fix and although I am a proud redneck, she would like a more elegant fix.
I tried the no acpi fix and it ruined the install. I admit it could have been me that screwed it up but I really want to fix her machine.
PLEASE HELP!

---

### Post by mjrclark on 2007-04-09
Slightly, though not much less redneck kludge if you have a dead old computer.  Take an old fan and plug it into the tsocket that the normal fan is plugged into. Then plug the normal fan into the system  fan power socket that should be unused. on my mobo it was about 7/8th the way up the left hand side, if the pc is lying down accessible side up.

---

### Post by scradock on 2007-05-06
Same problem - five year-old eMachines T1840. The cpu fan is slightly noisy, seems to run all the time in WinXP, but cuts out as soon as the grub boot starts with Edgy.

My BIOS is also old - August 2002, so very little ACPI support. I'm waiting to see if there is an upgrade available.

Until then I've succeeded in getting round the problem with BOTH "noacpi" AND "acpi=off" on the kernel line in the Grub menu.lst. I also used "irqpoll"  but I'm not sure that's essential - haven't tried without it.

Without "noacpi" or "acpi=off" - boots OK, shuts down after a while due to overheating;
with "noacpi" but not "acpi=off" -boots to brown screen and log-in, won't load gdm;
with "acpi=off" but not "noacpi"  - fails to boot, gets lost trying to assign IRQs;
with both  - boots and runs fine, fan stays on (audible), but no ACPI data available to monitor temperature. 

From what I've read, it seems that "acpi=off" tells the kernel not to enable ACPI at all, which leaves it confused when it tries to use ACPI to assign IRQs. "noacpi" forces it to use an alternative method to assign IRQs.....

My system doesn't even report sensible temperatures - the critical points are all around -270C (close to absolute zero!) and the reported temperatures is in that region also. The numbers are in /proc/acpi/thermal_zone/THRM/ as expected, but some translation step from sensor reading to number is obviously being mishandled.

hope that helps someone avoid the metal-cutting!
scradock

---

### Post by flightless bird on 2007-05-10
I hope this problem is resolved soon - I am having very similar problems with Feisty on my HP ze4315 laptop. It was working fine until I installed all the updates and now it shuts down within a minute of booting after reporting critical temperatures of ~40C.

---

### Post by bogdan.veringioiu on 2007-06-28
same here with amilo l1310 laptop.

---

### Post by Harkonnen on 2007-07-07
I would really like to know when this is going to be fixed.

My emachines T1840 cpu fan also won't come on once it passes the GRUB bootloader. Works fine in WinXP. Comes on in 6.06, but not anything with newer kernel version.

My motherboard is the same as the other guys, a Trigem Imperial either the GL or GLVE.

---

### Post by DarkPontiac on 2007-07-09
> **Harkonnen said:**
> I would really like to know when this is going to be fixed.

My emachines T1840 cpu fan also won't come on once it passes the GRUB bootloader. Works fine in WinXP. Comes on in 6.06, but not anything with newer kernel version.

My motherboard is the same as the other guys, a Trigem Imperial either the GL or GLVE.

I would like to know also... using the acpi=off command makes my internet not work..

I have the Imperial GL-VE and am trying this in 7.04

---

### Post by Harkonnen on 2007-07-09
> **DarkPontiac said:**
> I would like to know also... using the acpi=off command makes my internet not work..

I have the Imperial GL-VE and am trying this in 7.04

When I use acpi=off my usb peripherals won't work.

Its weird, I wonder if the new kernel will fix it.

[http://kernelnewbies.org/Linux_2_6_22#head-5d724bd616077cc8ca5366c00486dde560be6ce8](http://kernelnewbies.org/Linux_2_6_22#head-5d724bd616077cc8ca5366c00486dde560be6ce8)

---

### Post by DarkPontiac on 2007-07-09
> **Harkonnen said:**
> When I use acpi=off my usb peripherals won't work.

Its weird, I wonder if the new kernel will fix it.

[http://kernelnewbies.org/Linux_2_6_22#head-5d724bd616077cc8ca5366c00486dde560be6ce8](http://kernelnewbies.org/Linux_2_6_22#head-5d724bd616077cc8ca5366c00486dde560be6ce8)

When i used "irqpoll acpi=off" it seems to let me net work fine. Haven't tried any usb posts, although i have like 4 things connected lol. My webcam lights green so i am guessing it works. It usually lights red when the computer didn't detect it.

EDIT: I just connected my portable hard drive and it detected it and showed the files. I rather see this work without the added commands though....

---

### Post by Harkonnen on 2007-08-15
Any update or another possible solution to this problem?

Is it fixed with Gutsy?

It is really frustrating me trying to get this to work.

---

### Post by kamalmostafa on 2007-11-26
This post explains how I fixed the negative-temperature (-270 degrees C) and CPU fan problems on my eMachines system:
[INDENT]
[http://ubuntuforums.org/showthread.php?t=623633](http://ubuntuforums.org/showthread.php?t=623633)[/INDENT]

It may be of value to some of you as well.

 -Kamal Mostafa

---

### Post by Harkonnen on 2008-03-30
Well whadayaknow!

The new hardy heron beta doesn't have this problem for me anymore! I dunno what changed but WOOO!

---

