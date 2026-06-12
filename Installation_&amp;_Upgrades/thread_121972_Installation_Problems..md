---
title: "Installation Problems."
date: 2006-01-26
forum: Installation &amp; Upgrades
---

### Post by Dave_Man on 2006-01-26
hey guys..
I tried to install ubuntu on my PC for the first time, but after the ""Detecting hardware to find CDrom drive" it just stops and I have an empty blue screen with a white line at the bottom that I can write stuff in.
tried punching stuff on the kleyboard and found that ctrl+c restarts the hardware checking but still doesn't go past it.
tried googling but had no error code to search for so couldn't find anything.

anybody know what the problem is?
I tried it 4 times.
running from an official mailed-in CD - ubuntu 5.10 for intel.

My PC specs:
Intel p4 2.8Ghz
MSI motherboard
512MB dual DDR
Geforrce FX 5200
SATA hard drive 4 GB free
1 CDROM
1 sony CD burner

also have winXP installed.

help would be appreciated.
thanks.
Dave.

---

### Post by public_void on 2006-01-26
Have you tried a live CD to check if all your hardware is detected?

---

### Post by aysiu on 2006-01-26
The problem is probably:

1. Your installation CD is corrupt (yes, even if it's one of the official ShipIt CDs, this is possible).

2. It's trying for a screen resolution your monitor can't handle. If that's the case, try typing ```
boot vga=791
``` instead of just pressing Enter at the beginning.

3. Your hardware's screwy somehow.

---

### Post by Del UK on 2006-01-26
Which MSI mainboard and is bios upto date...........

How do you have boot sequence set in bios?

---

### Post by Dave_Man on 2006-01-26
Live CD works without problems.
BIOS isn't up to date.. i'll try that later
BOOT sequence is : CDROM, HD, Burner
will try the screen resolution thing.
thanks alot for the help.. i will try all these these things and keep ya posted..

thanks.
Dave.

---

### Post by Dave_Man on 2006-01-27
ok so..
I downloaded and burned a new CD and it still gives the same problem so its not a faulty CD..
I tried putting an ubuntu 5.04 CD and it did pass that stage.
so I have no idea what the problem is..
It sometimes gave me a problem with mounting the CD.. maybe that has something to do with it.

anyways.. I also updated my BIOS (its an AMIBIOS) didn't change anything.
I tried uding both CDROMs and no diffrence..

tried "boot vga=791" gave me a unknown image error.

so... any suggestions?
i'm getting desperate here...
Thanks.
Dave.

---

### Post by Ocxic on 2006-01-27
try also disableing power managment APM in the bios, it can cause problems with installers, freezing like that on some computers. you can turn it back on once your finsihed with the install.

---

### Post by 5-HT on 2006-01-27
Not sure if it's relevant to your situation, but I had a similar problem when trying to install breezy.

For me, the solution was to disable ACPI (similar to Ocix's suggestion of disabling APM) with the boot options:

```
 acpi=off noacpi 
```

That may be worth a shot.
If not, hope someone else around can give you a hand.


HTH

---

### Post by Dave_Man on 2006-01-28
tried acpi off and turning off apm in my bios.
after waiting a long time it gives out a: "can't mount the CD" error.
any more suggestions? this is my first time installing ubuntu so it might be a huge noob thing that i'm missing here..

Thanks.
Dave.

edit: OK.. now that I got this error message I did a search and found that others have the exact same problem..
they came up with a few solutions but none of them work for me..

the following threads talk about it:
[http://ubuntuforums.org/showthread.php?t=75155](http://ubuntuforums.org/showthread.php?t=75155)
[http://www.ubuntuforums.org/showthread.php?t=71671&highlight=cd+mount+breezy+install](http://www.ubuntuforums.org/showthread.php?t=71671&highlight=cd+mount+breezy+install)

any more suggestions would be greatly appreciated.

---

### Post by el3ktro on 2006-02-02
Can you just try to remove the CD burner, install, and if this doesnt work try to remove the CD drive and install again.

Tom

---

### Post by stemar on 2006-02-02
Try changing the disk controller settings. I had a similar problem and resolved it by change from "Auto" (the Bios making the settings it felt best) to "Enhanced" (supporting both SATA and PATA - I had a SATA drive and a CD-ROM).

---

### Post by compilerguy on 2006-02-21
Hello,

I'm having the same problem with my install: "Your installation CD-ROM couldn't be mounted". I've tried fiddling with all the different IDE settings in the BIOS. I've tried hooking up a different CD-ROM. I've tried two different install CDs. Nothing seems to work.

It seems like others have eventually solved this problem, but largely by trial and error. Is there someone out there who really understands what's going on here?

Any help would be greatly appreciated.

-Sam

My machine: Shuttle SD11G5 -- Intel 915GM, ICH6M chipset, Phoenix AwardBIOS 6.00PG

---

