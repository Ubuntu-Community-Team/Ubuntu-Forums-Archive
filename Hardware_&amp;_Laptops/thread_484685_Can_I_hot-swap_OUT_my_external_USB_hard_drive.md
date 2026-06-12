---
title: "Can I hot-swap OUT my external USB hard drive?"
date: 2007-06-26
forum: Hardware &amp; Laptops
---

### Post by cdupree on 2007-06-26
This weekend I replaced XP with Ubuntu 7.04.  Most things are working as expected, and the install was quite simple.

This is probably a silly question, but can I reliably hot-swap out my external USB hard drive?  I can hot-swap it in, but I can't find any posts or docs about hot-swapping it out.  Does one imply the other?

Thanks in advance for your time!

---

### Post by ramjet_1953 on 2007-06-26
All you need to do is right-click on the desktop icon that appeared when you plugged-in the external drive.

A drop-down menu will appear. Just select [COLOR="Blue"]Unmount Volume[/COLOR].

Regards,
Roger :cool:

---

### Post by cdupree on 2007-06-26
Hi ramjet_1953, thanks for your reply!

Problem is, the desktop icon for the disk appears when I hot-swap the drive in, and it has a drop-down menu.  But there's no Unmount.  There's an Eject, which didn't work.  I tried Unmounting from another menu (don't remember where but I can go find it) but I got a pop-up at the bottom right of the desktop saying that data was being written to the disk and I shouldn't remove it.  The pop-up never went away.

I'm probably missing something obvious, and I apologize for taking up time on something as basic as this, but having inadvertently wiped out a partition I intended to save through a typo, I'm being ridiculously cautious for a bit.

---

### Post by hardyn on 2007-06-26
if you enable the <edit>*feisty* backports and download the HAL update, it will then give you the option to "unmount" and won't to that un-mount remount thing with the error.

---

### Post by cdupree on 2007-06-26
Fool that I am ;) , I dunno what hardyn means.

"if you enable the edgy backports and download the HAL update, it will then give you the option to "unmount" and won't to that un-mount remount thing with the error."

Edgy backports?  I'm on Feisty Fawn.  Or is this "edgy" in a different context?  And what's HAL?  I thought that was 2001 :popcorn: ...

---

### Post by hardyn on 2007-06-26
System -> Admin -> Synaptic 

Settings ->  repositories -> updates: check Fiesty Backports (sorry i said edgy above, living in the past a little i guess)

Close -> reload

after a few seconds or a reboot, im sure you will be promped about new updates, one will be for the HAL (hardware arbitration layer) about 6-7 packages.

after install your cameras, and harddisks will unmount correctly.

cheers.

---

### Post by cdupree on 2007-06-26
It works.  Many thanks for all the advice and especially the patience! 

There's still no Unmount on the right-click drop-down on the desktop icon (what they call options menu in WinLand, is it the same name in Linux?).  But the Unmount command on the drop-down in File Browser works as you said it would.

I appreciate your help!

---

### Post by hardyn on 2007-06-26
I have a right click unmount... strange.

---

