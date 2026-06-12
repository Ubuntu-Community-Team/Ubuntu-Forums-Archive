---
title: "[Solved] Ubuntu won't boot after install: &quot;Alert! /dev/disk/by-uuid/**** does not exi"
date: 2009-07-30
forum: Installation &amp; Upgrades
---

### Post by peridot on 2009-07-30
I was going to post this, but after two days of beating my head against it, I stumbled on the solution mainly by brute force. I thought I'd post the solution in case it helps someone else. The solution? At the install screen, hit F6, highlight acpi=off, hit enter to put an x next to it, esc, then do the install as usual. That's it.

I have a new dell PowerEdge R610 with PERC 6/i raid1 server that I am trying to install Ubuntu 9.04 server on (though no other ubuntu works, suse did). The install runs perfectly, but when I reboot, it gives me this screen:
**********************************************************************
Boot from (hd0,0) ext3 2029ad8b-cfaa-42c1-9948-2396b66d8510
Starting up ...
Loading, please wait...
Gave up waiting for root device. Common problems:
 - Boot args (cat /proc/cmdline)
    - Check rootdelay= (did the system wait long enough?)
    - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/2029ad8b-cfaa-42c1-9948-2396b66d8510 does not exist. Dropping to a shell!


BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)
**************************************************************************

---

### Post by quixote on 2009-07-31
Hmm.  Interesting.  This is the 9.04 server version that gave you this grief?

---

### Post by Odin1979 on 2009-08-05
I had the exact same issue, the little trick worked great, thanks!

---

### Post by Liezl on 2009-08-06
Hi there, i was upgrading my system from v8.10 to v9.04 online, it prompted me to restart, which i did, i've been stuck at that screen for 2 days now, have tried everything! Only problem i have is, i dont want to lose any of my existing data and emails, if i do as u suggest, will all my stuff still be there, sorry for being a ninny, but i know absolutely nothing about this gibberish..... an dont want to lose all my work!!!!!!

---

### Post by quixote on 2009-08-06
Liezl: when you say "that screen," which screen do you mean?  The exact same one as the original question?  Some other grub error?  If so, which one?  Or does it spend some time booting, look like it's going to go to a login or desktop, and then go black?

To answer you main concern: no, your data won't be harmed if you, for instance, physically turn the computer off to regain control.  Reboot with a LiveCD.  That will allow you to see the hard drive that has your data on it, and you can back up the files you're particularly worried about.

Having said your data are okay, there is a very small possibility that's not true if the real problem has nothing to do with the install but is a symptom of, say, hard disk failure.

Assuming the problem is related to the install, then the two likeliest problems are either  

1) some kind of boot option incompatibility.  You could try the acpi=off option.  At worst, it won't help.  You can try booting into safe graphics mode.  If that works, it'll tell you that the problem lies somewhere in graphics.  xorg.conf or display settings.  

or

2) (and this I would think is the likeliest) grub has lost track of where its file of boot locations is.  In that case, you're probably getting something like "grub error 15".

---

### Post by quixote on 2009-08-06
I should add that your emails will be in a hidden directory in your home directory:

/home/your-user-name/.mozilla-thunderbird/a-bunch-of-random-alphanumerics.default/

You can select "show hidden files" on the nautilus "View" menu to see them all.

---

### Post by Fjan on 2009-08-18
Thank you! Brand new R610 owner here with the same problem. Your tip solved it. In the 4 hours I spent on it I did find another solution though: you can add "rootdelay=90" to the relevant kernel entry in Grub and it will eventually come up as well. By the way I have SAS 6iR RAID 1 (so the PERC may not be the problem) I wish Dell would start supporting Ubuntu

---

### Post by Fjan on 2009-10-31
Replying to myself in case someone else with the same problem ends up here. 

For Karmic Koala (9.10) the fix is different. After install exit from the Busybox. To get the Dell R610 to automatically load Ubuntu you have to edit /etc/default/grub
and add the line:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash rootdelay=90"

and then run grub_update (or update_grub can't remember)
(bug report for Grub2 has already been filed)

---

### Post by wbic16 on 2012-07-18
Note that if you edit /etc/default/grub, there are comments at the top of the file instructing you how to update grub.  See below.

> 
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


---

