---
title: "Cursor won't move!"
date: 2007-07-17
forum: Hardware &amp; Laptops
---

### Post by billgates27 on 2007-07-17
I installed Ubuntu 7.04 on Virtual PC. It booted up, but I can't move the cursor. What happened???? :confused:
ADDITION: The buttons don't work either.

---

### Post by billgates27 on 2007-07-17
COME ON!!! Will SOMEONE answer me??????????????????????????????????????????????????????????

---

### Post by david_2001 on 2007-07-17
> **billgates27 said:**
> COME ON!!! Will SOMEONE answer me??????????????????????????????????????????????????????????
Well, I for one know nothing about Microsoft Virtual PC - I run a Windows guest in a VM on a Linux host and not the other way around - and this may be the wrong place to ask about Microsoft software.  Why not try a Google search for: microsoft "virtual pc" linux guest mouse pointer.

---

### Post by akiratheoni on 2007-07-18
The first result for googling the term "mouse problem ubuntu 7.04" (without the quotes) comes up with the Virtual PC problem.

It's not an ACTUAL fix but involves you being able to control the mouse with the number pad.

[http://arcanecode.wordpress.com/2007/04/25/ubuntu-704-and-virtual-pc-2007-mouse-issue-workaround-sort-of/](http://arcanecode.wordpress.com/2007/04/25/ubuntu-704-and-virtual-pc-2007-mouse-issue-workaround-sort-of/)

Sorry I can't help any more. I'm quite new to Ubuntu but while browsing for a solution to my problem, I ran into this.

---

### Post by david_2001 on 2007-07-18
VMs usually provide some form of guest additions software that is installed and run in the guest operating system and does things like allowing the mouse to work.  Microsoft Virtual PC is no different.  The Google search indicates that Virtual PC only recently provided guest additions for a Linux guest and that they don't necessarily work with Ubuntu, amongst others.

---

### Post by billgates27 on 2007-07-18
> **akiratheoni said:**
> The first result for googling the term "mouse problem ubuntu 7.04" (without the quotes) comes up with the Virtual PC problem.

It's not an ACTUAL fix but involves you being able to control the mouse with the number pad.

[http://arcanecode.wordpress.com/2007/04/25/ubuntu-704-and-virtual-pc-2007-mouse-issue-workaround-sort-of/](http://arcanecode.wordpress.com/2007/04/25/ubuntu-704-and-virtual-pc-2007-mouse-issue-workaround-sort-of/)

Sorry I can't help any more. I'm quite new to Ubuntu but while browsing for a solution to my problem, I ran into this.

OK Thanks this helped a lot :)

---

### Post by raf2u on 2007-08-05
Have a look at [http://ubuntuforums.org/showthread.php?t=413899&referrerid=356303](http://ubuntuforums.org/showthread.php?t=413899&referrerid=356303) - there is a bug in the 7.04 kernel of Ubuntu (and other Debian). This is not a Microsoft Virtual PC or Virtual Server issue. There is a simple workaround - check that URL and look around the later posts (parameter i8042.noloop). Good luck...

R.

---

