---
title: "fsck on boot will not complete"
date: 2009-02-11
forum: Hardware
---

### Post by 5nak3 on 2009-02-11
I formatted my hard drive (using 8.04) and installed (8.10) however since then, I have not successfully been able to complete the fsck on system boot.

I get a certain percentage of the way through and the whole system freezes, no key combination does anything the HDD light stays on but the HDD does not make any sound to show it is being read. And I'm ultimately forced to hard reset the system.

I have no problems when using 8.10 in the desktop environment and doing a fsck through the live cd using:

sudo e2fsck -C0 -p -f -v /dev/sda1

or 

sudo e2fsck -y -f -v /dev/sda1

do not give me any bad sectors and complete without a problem.

I'm just wondering if anyone has any advice or knowledge as to what is going wrong on boot.

I do want to keep fsck but I don't want it to boot and freeze my system as I'm sure hard resets do no good to it...I even tried reverting back to 8.04 and running sudo touch /forcefsck to see if the fsck will complete under 8.04 and it also froze, despite never having any problems since October when I first installed ubuntu on the system.

---

### Post by 5nak3 on 2009-02-12
For the time being I have disabled fsck completely and will run it through the live cd...but I am worried that there is something wrong with the HDD which the live cd fsck does not pick up on.

Also something else I've noticed is that I tried shutting down the PC today, and for some reason when it exited the desktop environment it didnt initiate the shutdown sequence. The screen blanked out but everything else was still working from the looks of things. I wonder if this has anything to do with the fsck failing on boot...

---

### Post by 5nak3 on 2009-03-23
Hi all, just bumping this as this is an ongoing problem which i am having. As a result fsck has had to be disabled. I can run it via live cd or the gparted cd (i think) but I would rather have it done automatically on boot every 30 or so boots.

Anyone got any clues as to what the problem might be?

---

