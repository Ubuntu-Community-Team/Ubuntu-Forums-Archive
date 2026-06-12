---
title: "Can't boot from CD"
date: 2009-07-19
forum: Installation &amp; Upgrades
---

### Post by Deefex on 2009-07-19
hey, newbie here. hello to all. so this is my problem. i burned the 699mb file from the ubuntu website. in nero 6 i chose the burn image to disc.  so long story short, i even edited my BIOS for the 3 places to all load from cd rom. switched from the dvd drive to teh cd drive. nothing. just says "disk boot failure, insert system disk".  i'm working on the partitions now. having a hard time understanding how many i actually need for linux to run smoothly. but my question is, since i can't boot from the CD, can i install ubuntu from that .exe file that came with the .iso? thanks in advance

EDIT: ok this is how i'm going to go with the partitions
1st Logical partition 30gb ext3 file system (for /home)
2nd Logical partition 8gb ext3 (for / )
Swap 1400MB

---

### Post by ramnarayan on 2009-07-19
> **Deefex said:**
> hey, newbie here. hello to all. so this is my problem. i burned the 699mb file from the ubuntu website. in nero 6 i chose the burn image to disc.  so long story short, i even edited my BIOS for the 3 places to all load from cd rom. switched from the dvd drive to teh cd drive. nothing. just says "disk boot failure, insert system disk".  i'm working on the partitions now. having a hard time understanding how many i actually need for linux to run smoothly. but my question is, since i can't boot from the CD, can i install ubuntu from that .exe file that came with the .iso? thanks in advance

Not sure what's wrong - possibly your disk and something to do with the writing - but that too seems ok since you wrote it as an image

Does the CD work on your working system (is it correct to assume its windows)

If so yes the wubi.exe thingy will work

Pop the CD in - and then click on wubi to help you install Ubuntu

Also meanwhile check for how to write a cd at
[https://help.ubuntu.com/9.04/switching/installing-burning.html](https://help.ubuntu.com/9.04/switching/installing-burning.html)

and other help at

[https://help.ubuntu.com/9.04/index.html](https://help.ubuntu.com/9.04/index.html)

---

### Post by spcwingo on 2009-07-19
Did you check the md5 of the downloaded iso and burn at the slowest possible speed?

---

### Post by Deefex on 2009-07-19
yeah, you guys are right. something's wrong with the cd. i can't open it in windows. it says my f drive is not accessible when i have that cd in it. and no i didn't check the md5.

---

### Post by Deefex on 2009-07-19
i burned like 3 more cds. lol. anyways. sometimes in the middle of the install the screen would go black. then i thought it was cause of the cd. but after a couple of times of me happening. i just pressed enter and it went right back to where it was. i guess it's the screensaver. i'm still looking around. want to change some of the display setting. i'm in gnome, but i wanna try KDE. thanks for all the help.

---

