---
title: "Live CD does not boot after aborted install"
date: 2008-12-23
forum: Installation &amp; Upgrades
---

### Post by mulluysavage on 2008-12-23
Hi,

I tried installing Xubuntu from CD-ROM on a Compaq Presario 1700. I went for the "whole disk" option. The install hung 15% in for a good 30 minutes, and the pointer wasn't moving. So I did a hard restart.

Now all I get on boot is "Operating System not found." Completely understandable, but why doesn't the Live CD boot? I enetered the BIOS and made the CD-Rom the primary startup disk, but it doesn't even try. 

Have I created a doorstop, or is there some way around this?

Thanks!

Phil

---

### Post by oilchangeguy on 2008-12-23
> **mulluysavage said:**
> Hi,

I tried installing Xubuntu from CD-ROM on a Compaq Presario 1700. I went for the "whole disk" option. The install hung 15% in for a good 30 minutes, and the pointer wasn't moving. So I did a hard restart.

Now all I get on boot is "Operating System not found." Completely understandable, but why doesn't the Live CD boot? I enetered the BIOS and made the CD-Rom the primary startup disk, but it doesn't even try. 

Have I created a doorstop, or is there some way around this?

Thanks!

Phil

this should not be. but since it is, do you have another cd you can boot from (windows)? you can at least see if it will boot from a cd.

---

### Post by mulluysavage on 2008-12-23
Right? 

I just tried this with "Hiren's Boot CD" and got the same result.

---

### Post by oilchangeguy on 2008-12-23
> **mulluysavage said:**
> Right? 

I just tried this with "Hiren's Boot CD" and got the same result.

don't know if this will work. but, open the computer and remove the mobo battery. let it sit for at least an hour (to use any stored power from the bat) then install the battery, set the bios to boot from the cd drive. and see what happens.

---

### Post by mulluysavage on 2008-12-23
Interesting idea. Hopefully its not too  hard to get at (laptop.) The BIOS is just that-built-in, right? I can't replace it? This is hilarious.

---

### Post by jflaker on 2008-12-23
> **mulluysavage said:**
> Hi,

I tried installing Xubuntu from CD-ROM on a Compaq Presario 1700. I went for the "whole disk" option. The install hung 15% in for a good 30 minutes, and the pointer wasn't moving. So I did a hard restart.

Now all I get on boot is "Operating System not found." Completely understandable, but why doesn't the Live CD boot? I enetered the BIOS and made the CD-Rom the primary startup disk, but it doesn't even try. 

Have I created a doorstop, or is there some way around this?

Thanks!

Phil

Since it is an older system, try recording the disk at 4X.  I have had issues with older machines that can't read disks burnt at faster than 4X

---

### Post by bhaverkamp on 2008-12-23
Have you checked your BIOS boot order?

---

### Post by oilchangeguy on 2008-12-23
> **bhaverkamp said:**
> Have you checked your BIOS boot order?

you may want to read post #1 again. the op states they checked the boot order.

"I enetered the BIOS and made the CD-Rom the primary startup disk, but it doesn't even try. "

---

### Post by mulluysavage on 2008-12-23
It read from this disk succesfully enough before to enter installation and get several steps into it. Now... nothing. I am going canoing saturday, maybe i can use it as an anchor... or maybe there's a way to save this and load it with liunx... stay tuned...

---

