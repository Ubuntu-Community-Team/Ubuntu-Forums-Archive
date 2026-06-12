---
title: "Unable to boot from live CD"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by apparle on 2009-04-26
I wanted to do a fresh install of jaunty..........
Downloaded a live CD, checked the md5 sums....burned the CD, performed the integrity check.....all good.

When I boot into live CD...I don't even see the splash image of kubuntu or ubuntu (tried both live CDs) :confused:
I just see some hex numbers in the lower part of screen(black and white) and that's it. The booting just stops there.
Attached the images

I repeated the same procedure for alternate CD...when I started  install, all went well till the paritioning.
I selected manual partitioning. Here the partition table is not displayed at all, just the main hard disk and If I select it, it says "you have selected device. do you want to format it" or something like that.
I don't want to reformat complete hdd, just want to modify 1 partition.
Various other options like 'undo changs to partiton etc are also displayed'...........

Previous version it 7.10,8.04,8.10 CDs booted well...why can't I do it right now.
Also my friend installed from same CD and everything went on fine.


Note: the initial menu when CD boots up shows languages. When I select the language the languages don't disappear, just go into the background making it difficult to read the menu itself.

---

### Post by 123456789123456789123456 on 2009-05-03
Interesting, what is the computer configuration/hardware.
something on the video side, seems to be affecting something in 9.04
What is the hard drive partitions, and file systems on it?

---

### Post by stinkeye on 2009-05-03
I had the same problem and was able to install using the f6 option and marking acpi=off.Had a few error messages and then the live cd booted.
I've got no idea what acpi is and I dont have this problem with the 8.10 live cd.

---

### Post by rebski on 2009-05-04
There are several, i.e. too many, threads on this very issue. It is a shame that we don't make the effort to keep them all together.

Here is another which corresponds to the experience posted here
[http://ubuntuforums.org/showthread.php?t=1134107](http://ubuntuforums.org/showthread.php?t=1134107)

Yet another here
[http://ubuntuforums.org/showthread.php?t=1148025](http://ubuntuforums.org/showthread.php?t=1148025)

hi apparle, thanks for posting the screen shots. I have  difficult in getting this verbose information, mine are obscured by the splash screen and I am not sure how to lose the splash so as to see what is going on.

---

### Post by apparle on 2009-05-05
My problem is solved............I just used the option "Load fail safe options" in my BIOS and was able to boot smoothly

---

