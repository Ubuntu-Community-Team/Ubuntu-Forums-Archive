---
title: "Problem with USB Drive"
date: 2005-03-09
forum: Hardware &amp; Laptops
---

### Post by Nenad on 2005-03-09
I have just recently installed Ubuntu, and I find that my USB drive (128Mb, LG) does not even get detected (no sda entry in dev). The same things happens under Mandrake.

I have tested the drive on a friends PC (also running Ubuntu.... Do I get bonus points for introducing him to it?), and it got auto-dtected without any problems.

Any suggestions?

Also, I have two on-board usb ports, whihc Ubuntu does detect, and a PCI card with two more, which do not get detected.

---

### Post by Titanium on 2005-03-09
We might have the same problem. Please read [this](http://www.ubuntuforums.org/showthread.php?t=17946) thread and see if the symptoms are the same.

---

### Post by macewan on 2005-03-09
http//www.ubuntuforums.org/showthread.php?t=17946

---

### Post by DrTiger on 2005-03-09
I can't follow the link, because I am redirected at the microsoft site *every* time -.-

---

### Post by alastair on 2005-03-09
"I can't follow the link, because I am redirected at the microsoft site *every* time -.-"

Ha - I was going to laugh! What!?!

But ... I was as well!

So, try this (fingers crossed) :

[http://www.ubuntuforums.org/showthread.php?t=17946](http://www.ubuntuforums.org/showthread.php?t=17946)

The links before were formatted slightly wrong - but what's with the microsoft.com redirect? Weird.

---

### Post by alastair on 2005-03-09
OK - it's firefox doing an "I feel lucky" at Google on the address like "http" (only). Odd.

---

### Post by Nenad on 2005-03-10
IT does sound similar, but it still does not get detected when I try to plug it into the back of the MB (If it is plugged in during boot, it simply hangs, if I try to plug it in once I have booted nothing happens, I will check dmesg when I get back to that computer)

---

### Post by sadneophite on 2005-04-16
I had the same problem : 

[http://www.ubuntuforums.org/showthread.php?p=135077](http://www.ubuntuforums.org/showthread.php?p=135077)

solved it with putting

'acpi=off' after 'splash' in my grub options

---

### Post by lorap on 2005-04-16
hi friend!
i think i know the solution for your problem.
let's work it out.
you say your usb drive wasn't recognized,well it's ok anyway :-)
create a directory "usb-drive" in "/home/yourusername" folder:

sudo mkdir /home/yourusername/usb-drive

now let's get your usb drive connected:

sudo mount /dev/sr0 /home/yourusername/usb-drive -t vfat -o umask=000

that should work :-)
but remember,if you run hoary then you should change "sr0" to "sda0" and if your hard drive formatted as ntfs then change "vfat" to ntfs.
something else...
open "/dev" directory and then plug in and out your drive watching what devices appear and disappear in it.if you have a power button then just turn the power on and off.
have a nice day friend!
pavel

---

