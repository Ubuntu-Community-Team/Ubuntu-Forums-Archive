---
title: "Can't install, acpi_pss errors"
date: 2009-07-03
forum: Installation &amp; Upgrades
---

### Post by smakand on 2009-07-03
Hey all, I've been using linux (as primary) for a few years now on my laptop and past desktops, but I've recently tried to install some version of linux on my gaming desktop to experiment with some things.

I have a k9a2 platinum mother board, ( [http://bit.ly/Tzhzi](http://bit.ly/Tzhzi) ) and I originally tried to install fedora 11, which claimed to be missing a cd-rom driver, and then ubuntu studio 9.04, which also claimed to be missing a cd-rom driver.

I'm now onto trying Ubuntu 9.04, and it reports an error similar to this:

> > Powernow-K8: Your BIOS does not provide ACPI_ objects in a way that LINUX understands. Please report this to LINUX ACPI_ Maintainers. I tried installing without any f6 options, and with checking 'acpi=off', and with checking 'acpi=off, noapic, nolapic'. Checking all three of these reports an apci not found? (Will update with proper error message).

All the searching I've done has had answers involving raid drivers, I am not running a raid of any sort, and the solutions to these problems involve compiling a kernel with some modifications, I'm not really up to doing that, especially if it's not garunteed to even be related to my problem.

The other thing I notice is that the motherboard reports an error > No array is defined, press cntrl-f to enter fast boot utility, it has always done this and has never posed a problem for various windows installs. I tried pressing ctrl-f, but none of the options work (unresponsive), and I end up just exiting.

Thanks for your help!

Specifications for motherboard:
[http://us.msi.com/product/p_spec.asp?model=K9A2_Platinum&class=mb](http://us.msi.com/product/p_spec.asp?model=K9A2_Platinum&class=mb)

---

### Post by smakand on 2009-07-03
Alright, slight update. I notice that these errors flash on the screen before the Ubuntu installer dumps me into BusyBody? terminal, which says to me maybe these issues aren't what's stopping the install.

---

### Post by NaseEder on 2009-07-08
same problem here.

msi k9a2 cf , hd3800 + hd3400 , 6gb ram

bios: 1.7

i will try another bios.. better not 1.9 as i read from other posts.
from the beginning i had a reboot problem with this board. it would only boot when reseted, no soft reset or reboot from OS..
had running windows xp 64 most of the time, some annoying blue screens appeared daily, especially after boot up. when running, it had almost no problems.

greets

---

### Post by NaseEder on 2009-07-08
with the new bios 1.A1 from MSI homepage, now i can reboot :)

but for now windows xp 64 doesn't want to boot up properly..
lets see if ubuntu 9.04 64 bit setup will work. looks like they are messing some things with their bios's

---

### Post by NaseEder on 2009-07-09
it's not working. ( ubuntu 64 setup, xp64 runs just fine as it should )

next thing i'll try is Ubuntu 32 Bit.
Maybe the problem is the additional IDE controller that is plugged into pci .
install harddisk is connected to onboard sata.. so this shouldn't be too much of a problem.

---

### Post by smakand on 2009-07-12
Keep me updated buddy. I'm using bios 1.3 because I have no floppy drive to update with, I can get one though and try. xp x64, vista x64, and win 7 RC x64 have all installed fine for me. I don't have an additional IDE controller plugged in, my primary HD is sata, and my cdrom is IDE.

---

### Post by NaseEder on 2009-07-13
it's weird... i don't get what is wrong or defect.

sometimes xp64 boots up normally, but if i start using the system a little bit too early, i will 100% get blue screens.
if bootup is past some specific point, i can do everything without problems.

ubuntu 32 didn't install either.

I removed the controller card and for now ubuntu 9.04 64bit seems to install as it should.
the controller chip's name is "sil0680"

i'll keep on trying..

---

### Post by NaseEder on 2009-07-13
it stopped after choosing the 200gb harddisk as install volume.

now i am running the installation from the livecd system..
its doing more than it ever did.. but lets see

---

### Post by NaseEder on 2009-07-14
for now I have Ubuntu 32Bit running.. no final state for 6gig ram...

when switching from Desktop to console (strg+alt+f1)
I found out those ACPI_PSS errors are still there..

I think they were gone when disabling ACPI in BIOS.. 
.. might be, I'll just kick the MSI-Board and try some other Vendor :D

---

### Post by smakand on 2009-07-14
Wait, so it's installed even with these errors? Hm, that implies something else is preventing the install on my computer. That actually helps me a lot if you say it can work even with these errors. Thanks.

---

### Post by NaseEder on 2009-07-16
yes, 32 Bit Ubuntu is running fine.

i decided to wait if some patch or update will appear, or maybe even just buy a Board from another Vendor, and maybe get some extra power.. but not now.

since i got stuck with 64 Bit, even Debian Core 502 64 Bit didn't like the system, for now i am trying to solve my multiscreen configuration..
there appear some problems with the two ATI HD38x0 Cards and multihead setups.. need to figure this out too.

---

### Post by NaseEder on 2009-07-24
allright.

got a new board and even ubuntu 9.10 64-Bit is running nicely.

when my new cpu arrives, i am going to check what exactly causes the problem.
could be:

RAM:    (2x2 + 2x1 = 6GB, different vendors)
Board:   MSI K9A2-CF
HDD:     Samsung 200GB

CPU and graphicsboard are running fine.
in the end it just turns out, the mixed ram modules are causing all the trouble..

you checked your ram stuff?

---

### Post by d4rk5h4dow5 on 2009-09-07
> **smakand said:**
> Hey all, I've been using linux (as primary) for a few years now on my laptop and past desktops, but I've recently tried to install some version of linux on my gaming desktop to experiment with some things.

I have a k9a2 platinum mother board, ( [http://bit.ly/Tzhzi](http://bit.ly/Tzhzi) ) and I originally tried to install fedora 11, which claimed to be missing a cd-rom driver, and then ubuntu studio 9.04, which also claimed to be missing a cd-rom driver.

I'm now onto trying Ubuntu 9.04, and it reports an error similar to this:

I tried installing without any f6 options, and with checking 'acpi=off', and with checking 'acpi=off, noapic, nolapic'. Checking all three of these reports an apci not found? (Will update with proper error message).

All the searching I've done has had answers involving raid drivers, I am not running a raid of any sort, and the solutions to these problems involve compiling a kernel with some modifications, I'm not really up to doing that, especially if it's not garunteed to even be related to my problem.

The other thing I notice is that the motherboard reports an error , it has always done this and has never posed a problem for various windows installs. I tried pressing ctrl-f, but none of the options work (unresponsive), and I end up just exiting.

Thanks for your help!

Specifications for motherboard:
[http://us.msi.com/product/p_spec.asp?model=K9A2_Platinum&class=mb](http://us.msi.com/product/p_spec.asp?model=K9A2_Platinum&class=mb)

So I don't know if this is a solved issue... if so I can't seem to find it but I'm getting this error message but only after I install updated drivers from nvidia 185. I can install Ubuntu 9.04 just fine and run my apache server no issues but soon as I update to any of the nvidia drivers (desktop effects call me dumb but I love em) and reboot I get the ACPI_PSS error

Spec:
Asus MB
Two Nvidia 7600gt (SLI enable on windows partition if that matters) 
3gb ram 

Any help or direction would be great. Maybe cause of two video cards? I just don't know lol

---

