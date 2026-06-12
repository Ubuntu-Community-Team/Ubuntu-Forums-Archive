---
title: "hp 500 laptop - feisty occasionally hangs for 5-10 secs"
date: 2007-07-06
forum: Hardware &amp; Laptops
---

### Post by topbot on 2007-07-06
Hi everyone,

I have an HP 500 laptop, which occasionally hangs for 5-10 secs every hour or so. Mouse pointer can be moved but windows only respond after these 5-10 secs are over. The system kind of accumulates all mouse clicks I made when it was hanging. I have it in Feisty and before that had it in Edgy, both Gnome and KDE. I do not have this weird behavior in Windows or FreeBSD on the same machine. The memory bank was thoroughly tested, so it is not faulty memory. Please help.

---

### Post by fredj on 2007-07-06
This happens on my Samsung Q35 laptop as well. I have no idea what the cause is at present. I will have to
switch to my other computer and see if it happens there as well or if it is specific to laptops.

---

### Post by clay_in_nj on 2007-07-07
So, I'm not alone. Get the same thing running Kubuntu Feisty on my System76 Gazelle Value.

-Clay in NJ

---

### Post by PaulFr on 2007-07-07
Any one or all of you accessing large files (say, copying files or viewing large videos) during that hour ? I answered a post recently ( **[http://ubuntuforums.org/showthread.php?t=489719](http://ubuntuforums.org/showthread.php?t=489719)** ) where the OP indicated that due to Linux file caching strategy, the kernel buffers the blocks of the large file throwing out other applications cached data; so when the copy / movie is finished, other applications are slow in responding. Does this ring a bell ?

---

### Post by topbot on 2007-07-07
nope. In fact, I found the problem. In my case it was the faulty firmware of my DVD drive, TS-L632D, which made it occasionally irresponsive to system queries. Reflashing the DVD made the problem disappear.

Thx everyone.

---

### Post by fredj on 2007-07-07
That is a valuable post. My Samsung Q35 also has a TS-L63D. How did you get the software for the 
reflash?

---

### Post by suoko on 2007-07-29
I have this problem with my ASUS A6F laptop too.
I'll try to see if I can find any firmware updates...
However edgy didn't cause this problem

I've installed feisty twice:
1st time it was an edgy -> feisty upgrade. 
2nd time was a fresh feisty install
The 1st time I also tried to upgrade to gutsy hoping it was a kernel bug, but the problem was still there.
I must say this bug is VERY ANNOYING because you end up with an unusable PC very often.
Moreover I thought INTEL hw was well supported...

---

### Post by holvenstot on 2007-07-29
You know, I had a problem very much like this which corrected itself when I moved from using the integrated video chip on my motherboard and moved to a real video card.  

Yes, I know that I am talking about a desktop and you are using a laptop and thus can't do anything about it.

BTW - it only happened when I would use the vendor supplied accelerated driver - it would work fine if I dropped back to the standard GPL'ed diver which came with X.

It was as if the system was missing an interrupt and you had to wait for a time out to occur before things got back to normal.

One interesting point I noted is that when ever this happened I would note that during the time of the hang the system monitor wold show that the CPU had been at 100% (when it came back - there were no display updates during the hang)

Just something you might want to check

---

### Post by suoko on 2007-07-29
just found out this:
when it's in the "hang mode" I can do some things like moving the mouse as well as see a shell (CTRL+ALT+F1)
While on the shell (which was also stuck) I saw the following messages (which I recovered from dmsg):

[  155.408000] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  155.408000] ata1.01: cmd a0/01:00:00:00:00/00:00:00:00:00/b0 tag 0 cdb 0x25 data 8 in
[  155.408000]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[  162.412000] ata1: port is slow to respond, please be patient (Status 0xd0)
[  185.432000] ata1: port failed to respond (30 secs, Status 0xd0)
[  185.432000] ata1: soft resetting port
[  185.784000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[  185.796000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[  185.796000] ata1.00: configured for UDMA/100
[  185.980000] ata1.01: configured for UDMA/33
[  185.980000] ata1: EH complete

any clue? It seems an HD problems.
As you can see it states 30 secs, which is the time of hanging..

I already tried disabling wireless drivers, intel drivers (using vesa) and so on.

just found the bug:
[https://bugs.launchpad.net/ubuntu/+bug/104581](https://bugs.launchpad.net/ubuntu/+bug/104581)

---

### Post by fredj on 2007-07-30
No, seems like the DVD or CD is causing it, try to find updated firmware for your drive.

---

### Post by suoko on 2007-07-30
It seems solved thanks to the solution suggested by Povoledo:

I've solved the problem editing /etc/initramfs-tools/modules, and adding this lines:

piix
ide_generic
ide_cd
ide_disk

# blacklist bad driver
blacklist ata_piix

# prevent unnecessary modules from being loaded (you don't need to do this)
blacklist ata_generic
blacklist libata
blacklist scsi_mod

after editing:

sudo update-initramfs -u

---

### Post by suoko on 2007-11-17
SOLUTION IS HERE:
[https://bugs.launchpad.net/linux/+bug/75295/comments/97](https://bugs.launchpad.net/linux/+bug/75295/comments/97)

thanks all

---

