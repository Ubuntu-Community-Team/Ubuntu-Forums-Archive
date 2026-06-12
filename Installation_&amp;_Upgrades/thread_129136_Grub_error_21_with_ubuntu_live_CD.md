---
title: "Grub error 21 with ubuntu live CD"
date: 2006-02-13
forum: Installation &amp; Upgrades
---

### Post by red_erik on 2006-02-13
G'day,

Although the NEC versa M540 is listed as OK by the Laptop Testing Team, for Hoary and Breezy, attempting to boot from the vesion 4.10 live cd causes GRUB to grumble that the "selected disk does not exist". (This is during "Loading Stage 1.5")

So far I've uncovered two proposed fixes:
1) [http://lists.gnu.org/archive/html/bug-grub/2003-02/msg00082.html](http://lists.gnu.org/archive/html/bug-grub/2003-02/msg00082.html)
suggests fiddling Type and Mode for Primary Master and Primary Slave. Unfortunately the "Insyde Software SCU" BIOS does not appear to possess such bios menu subjects, let alone "user" and "LBA" options.

2) [http://ubuntuforums.org/archive/index.php/t-17529.html](http://ubuntuforums.org/archive/index.php/t-17529.html)
The suggestion to "Download the ISO CD-image." of Smart Boot Manager 3.6 is complicated by absence  of such from: [http://btmgr.webframe.org/index.php3?body=download.html](http://btmgr.webframe.org/index.php3?body=download.html)

Now for the tricky bit. There is a belief here that a (probably older) live CD did fire up on an older versa M540. While googling, I did stumble across one poster who had "errror 21" problems with one CD drive, but succeeded with another brand of drive, on the same machine. (A bit complicated on a laptop, though.)

Maybe I should try to locate & download 5.10, cross my fingers, and hope for a change in fortune? (But it'll use grub too, I figure. :-(

Erik

---

### Post by tseliot on 2006-02-13
[QUOTE=red_erik]G'day,

Although the NEC versa M540 is listed as OK by the Laptop Testing Team, for Hoary and Breezy, attempting to boot from the vesion 4.10 live cd causes GRUB to grumble that the "selected disk does not exist". (This is during "Loading Stage 1.5")...

...Maybe I should try to locate & download 5.10, cross my fingers, and hope for a change in fortune? (But it'll use grub too, I figure. :-(

Erik[/QUOTE]
Try Breezy 5.10 which should (actually it does) support more chipsets than Warty as it has a newer kernel (2.6.12).

And perhaps you won't have that error.

---

### Post by red_erik on 2006-02-13
tseliot,

You were right, the ubuntu 5.10 live CD succeeds with the NEC versa M540 laptop, where version 4.10 was not compatible. Nifty! Now I can move to ubuntu at work, as I've done at home.

Thanks,
Erik

P.S. Sorry, I haven't yet figured this GUI sufficiently to quote your reply.
       (Now, if I subscribe to email notification, maybe I can use mutt for this    list too.)

---

