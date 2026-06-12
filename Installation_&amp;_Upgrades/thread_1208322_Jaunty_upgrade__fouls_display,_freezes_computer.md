---
title: "Jaunty upgrade  fouls display, freezes computer"
date: 2009-07-09
forum: Installation &amp; Upgrades
---

### Post by nanogeek on 2009-07-09
Hi,
I upgraded last night from Intrepid to Jaunty.
When I rebooted this morning for the new install things went well until I got to what should have been my desktop. At this point the display showed my old desktop wallpaper, compressed in width, displayed in multiple stripes, overlayed with alternating white vertical lines. The mouse is frozen. The keyboard does not respond

After rebooting repeatedly, I was able to overcome this problem by pressing escape during the grub load and selecting an older kernel. (the bottom one on the list that wasn't rescue) At least I think that is what happened.

I would like to know what the problem is, and how to resolve it permanently, so that I don't have to catch the grub menu on boot up, and so that my wife and kids won't have to deal with this.

I am running 9.04 32 bit on an old Pentium 3 (Coppermine) with 512 RAM, on board Intel video support.

Any help would be greatly appreciated.

Nanogeek

---

### Post by JohnLau on 2009-07-09
What is the exact model of your chipset?
I think you can set the default kernel to boot by [installing the package startupmanager]("https://help.ubuntu.com/community/StartUpManager")
[Have you tried upgrading the kernel to 2.6.30? ]("http://compustorm.no-ip.org/2009/07/boost-ubuntu-performance-by-installing-2-6-30-kernel/")It might help as well :popcorn:

---

### Post by caco on 2009-07-09
If you have a separate /home partition why not perform a fresh installation of jaunty
ps: Do be careful though when partitioning

[[IMG]http://brainstorm.ubuntu.com/idea/20470/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/20470/)

---

