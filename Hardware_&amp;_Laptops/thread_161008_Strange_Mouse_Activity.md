---
title: "Strange Mouse Activity"
date: 2006-04-16
forum: Hardware &amp; Laptops
---

### Post by Titus A Duxass on 2006-04-16
Something odd happened to my mouse on the Myth box that I have just built.

I connected the sound card line out to my amplifier and the mouse stopped!

Rebooting, trying the semi-automagic reconfigure of xorg and replacing xorg.conf with back up copy all failed to produce a working mouse.

On the umpteenth restart the system went through some checks.  Something to do with the drive had been or not been mounted correctly for over 30 cycles (or something like that).  This action seems to have been carried out in each drive (partition as I only have one drive with two partitions therefore two drives) and now the mouse works again.

What was this test and can I invoke it at some stage if the mouse stops again?

Thanks
Titus

---

### Post by dermotti on 2006-04-16
The test happens automatically after 30 reboots, its natural dont worry. 

The mouse thing? I dunno...usually a **sudo dpkg-reconfigure xserver-xorg **will clear that up.

---

### Post by Titus A Duxass on 2006-04-16
Can I get this test to start by a manual action?

Dpkg-reconfigure xserver-xorg did not clear the problem.

---

### Post by Titus A Duxass on 2006-04-16
The mouse has stopped again, this time for no apparent reason.
Again I have tried:

Rebooting,
dpkg-reconfigure xserver-xorg,
replacing the xorg.conf file with a back up copy.

Everything looks in order in the xorg.conf file.

The wireless mouse was replaced with a cable version, no change.

USB ports do not respond to the insertion of a USB mouse.

---

### Post by Titus A Duxass on 2006-04-23
Solved this problem - threw the motherboard (elitegroup K7S5A) away!
It had lost the USB functions and the mouse worked 1 of 10 boots.

Changed it for a AS Rock K7VT4A+ (30 euros) and apart from resetting the BIOS requirements I did not need to do anything, amazing.

---

