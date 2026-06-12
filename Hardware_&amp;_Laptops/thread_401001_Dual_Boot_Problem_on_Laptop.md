---
title: "Dual Boot Problem on Laptop"
date: 2007-04-04
forum: Hardware &amp; Laptops
---

### Post by Scyythe on 2007-04-04
I'm using a Toshiba U205-S5057 which came with Vista Home Premium. I partitioned the hard drive, and installed Ubuntu 6.10.
I had it installed a couple of days ago, but had to format and reinstall both operating systems.

My problem now is that the boot manager never comes up.
It boots straight into Windows without asking.
For a while after I had installed Ubuntu, when I restarted it would boot into Ubuntu without asking, then for a couple reboots it showed the boot manager, now it just goes straight to Windows.

I changed the default OS that's selected in the boot manager, but even before I did that the boot manager wasn't showing up.

Any ideas?
Thanks.

---

### Post by jjordan on 2007-04-04
I would guess that you reinstalled Windows after you installed Ubuntu.  Most likely the problem is that Windows overwrote your Master Boot Record (MBR) Grub has to put a stub in your MBR so that the computer sees that first.  Reinstalling Windows will overwrite this, some anti-virus software will also overwrite this trying to protect you from MBR viruses.  If you are running an antivirus program under Windows turn off  MBR protection or if you have the option update the anti-virus programs copy of your MBR so that it reflects the one with GRUB.  

This link tells you how to restore GRUB to your MBR:
[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

-j

---

### Post by jjordan on 2007-04-04
OOps, sorry! I should have read your post more carefully.  When you used the Windows boot manager to select an operating system it overwrote your MBR.  The remainder is the same.  When you get it working, edit the GRUB menu.lst to change the default operating system NOT the windows boot manager.

- j

---

### Post by Scyythe on 2007-04-04
Sorry I wasn't more clear; Ubuntu was installed after Windows.
Menu.lst is the file I used to change the default boot order.

I followed the directions in your first post, but it says not to format the partitions. Well when I get to the point to mount the partitions, I can't continue because it says:
     "Filesystems used by the system (/, /boot, /usr, /var) must be reformatted for use by this installer. Other filesystems (/home, /media/*, usr/local, etc.) may be used without reformatting."

---

### Post by jsr on 2007-04-15
yeah! me too having the same problem with this laptop U205-S5057, I could not figure it out yet... 
a cold boot should show up the grub menu.. check that...

---

### Post by Jagunço on 2007-04-18
It seems to be a problem with Toshiba laptops, perhaps.
My S-5057 behaves the same way.  :(

---

