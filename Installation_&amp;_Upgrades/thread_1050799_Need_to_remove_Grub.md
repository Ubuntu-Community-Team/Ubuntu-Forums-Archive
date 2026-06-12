---
title: "Need to remove Grub"
date: 2009-01-26
forum: Installation &amp; Upgrades
---

### Post by Sticky on 2009-01-26
Please don't flame me for this one.

I have a need to install Windows XP for a short period of time onto a system I've been running Linux on for a while now.  I don't have a proper Windows XP disc as such, only the system restore discs that I created when I first got the laptop and set it up.

I had Ubuntu installed on the only partition on the drive so I simply ran the restore discs and installed Windows over the top.  Great I thought.  One problem, the machine now won't boot as it still has Grub in the boot loader and I get a failure message.  I'm guessing it's failing becuase it's looking for Ubuntu which is no longer there.

Having browsed the web I find various suggestions about running F:disk etc which doesn't help me as I don't have any way of accessing it (as far as I know) on my system restore discs.  Can anyone offer any suggestions as to how I can remove Grub?

I have three machines in total and all three have been running Ubuntu for over a year now.  I still intend to stay with Ubuntu but I have a short term requirement for Windows.  Please help.

:(

---

### Post by Elfy on 2009-01-26
You need to restore the win boot - as you have no xp discs then try using supergrub, download, burn as iso and boot. 

It has option to fix your win boot.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by Sticky on 2009-01-26
Thank you - I'll try it this evening :)

---

### Post by Sticky on 2009-01-26
That's brilliant - it worked - I'm replying from that particular laptop (back in ubuntu :D)

---

