---
title: "Lucid suspend and resume problems"
date: 2010-05-07
forum: Hardware
---

### Post by clevertomato on 2010-05-07
Is anyone else having problems with suspend and resume on a laptop with ATI GPU and Lucid? I got things working great in Karmic using NOAPIC at grub but nothing I try gets proper suspend and resume in Lucid on my Dell Studio 1555 with ATI Mobility Radeon HD 4570.

---

### Post by ndstate on 2010-05-07
I am having the same problem with suspend and hibernate with the ATI Mobility Radeon HD 3400 Series.  Any ideas?

---

### Post by pmos69 on 2010-05-07
File a bug report, or mark a current bug as affecting you too.

Here's the opne I filed (although not ATI specific)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568711](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568711)

---

### Post by ndstate on 2010-05-07
shawnboy, check and see if your swap is mounting on boot.

A quick way to check is

```
free -m
```

Mine wasnt and I think that was causing some of my issues.

---

### Post by clevertomato on 2010-05-10
pmp6nl: yes, my swap is mounting at boot.

---

### Post by kinsago on 2010-05-10
Hi.

I've literally logged in to report the same bug on my IBM X31. It's almost enough to make me go back to debian (Karmic didn't like my laptop at all!!!)

Total noob so forgive me please...

---

### Post by efflandt on 2010-05-10
I have an older ATI X1300 on my desktop and had no problem with suspend or hibernate with default video drivers in 9.10.  In 10.04 LTS suspend would shut off the hard drive, but video remained on (blank) and power remained on.  Hibernate would save to swap and then everything remained running including hard drive and blank screen that was still on.

Since someone mentioned that suspend/hibernate issues may be a video issue (especially since video remained on), I tried **radeon.modeset=0** kernel parameter for user mode video instead of the new kernel mode video (kms), and then suspend and hibernate worked.  The **nomodeset** parameter is specifically mentioned as a general fix if someone has video issues when booting.  So maybe that does the same thing to disable kms for "any" video that has a kernel mode driver.

[http://www.ubuntu.com/getubuntu/releasenotes/1004#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture](http://www.ubuntu.com/getubuntu/releasenotes/1004#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture)

---

### Post by kinsago on 2010-05-12
> **efflandt said:**
> I have an older ATI X1300 on my desktop and had no problem with suspend or hibernate with default video drivers in 9.10.  In 10.04 LTS suspend would shut off the hard drive, but video remained on (blank) and power remained on.  Hibernate would save to swap and then everything remained running including hard drive and blank screen that was still on.

Since someone mentioned that suspend/hibernate issues may be a video issue (especially since video remained on), I tried **radeon.modeset=0** kernel parameter for user mode video instead of the new kernel mode video (kms), and then suspend and hibernate worked.  The **nomodeset** parameter is specifically mentioned as a general fix if someone has video issues when booting.  So maybe that does the same thing to disable kms for "any" video that has a kernel mode driver.

[http://www.ubuntu.com/getubuntu/releasenotes/1004#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture](http://www.ubuntu.com/getubuntu/releasenotes/1004#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture)

Tried this and, funnily enough, it gave me the same video issue I had with Karmic. Still no fix for suspend etc though :(

---

### Post by clevertomato on 2010-05-12
I also tried **nomodeset** with no success. I'd be happy to report this as a bug or mark one as effecting me, but I'm not sure how best to go about making a new bug report or which existing one to mark as effecting me.

---

### Post by clevertomato on 2010-07-26
Any progress on this? I've been waiting and waiting, occasionally booting into Lucid (instead of Karmic) on my still-very-new Dell Studio 15 with ATI Mobility Radeon 4570, applying updates as they are available, with no solution in sight for this suspend problem. It's a real drag not to be able to suspend a notebook computer, and a problem that I'd think would've been addressed by now.

---

### Post by clevertomato on 2010-07-27
I got around to trying AMD's Catalyst drivers version 10.6 and that seems to fix things. Woohoo!

---

### Post by johnnyrevell on 2011-10-09
nomodeset in grub solved it for me thanks! Even with a second monitor connected

Lucid 10.04, HP zd8000 laptop, VGA compatible controller: ATI Technologies Inc M24 1P [Radeon Mobility X600] , open video driver

add nomodeset to grub config:
edit /etc/default/grub
add nomodeset to GRUB_CMDLINE_LINUX
run sudo update-grub

Use Fn F5 to suspend

my xorg.conf :
Section "Screen"
	Identifier	"Configured Screen Device"
	Device	"Configured Video Device"
	SubSection "Display"
		Virtual	3040 1024
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

---

