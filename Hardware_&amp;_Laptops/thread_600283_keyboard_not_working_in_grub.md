---
title: "keyboard not working in grub"
date: 2007-11-02
forum: Hardware &amp; Laptops
---

### Post by dzza on 2007-11-02
Hi, I've spent the last hour browsing through previous posts and cannot find any solution for this problem:

I have a two OS's installed, and I really only use the ubuntu partition (other is opensuse 10.2).  Everything has been running fine when suddenly my keyboard stopped working doing boot up.  I cant access the bios setup (no response whatsoever to any keys being pressed)  and I cannot select to boot different OS's because pressing up/down doesn't do anything.  The keyboard is definitely on, because num lock still lights up and responds.  Then, after the os is loaded, the keyboard returns to full functionality.  

Again, no software/hardware changes have been made during the period of time in which this happened.  

The keyboard has a ps/2 connection, NOT usb.  

I have tried connecting/disconnecting the keyboard, restarting, etc, and none of that does anything.  

Ubuntu is the partition I use for most everything, and it is the one with all of my files on it.  Unfortunately I cannot select this partition, so at the moment I am very screwed.  

Thank you for any help you can offer.
Dave

---

### Post by spier on 2007-11-02
Well, I was ready to tell that an USB keyboard would act like this, but a PS2 ...

Just some thoughts:

If I read it correctly, you are booting in Suse's partition. Is  /boot/grub/menu.lst in this partition or, if in ubuntu, do you have mount rights on that partition?  In any case, maybe increasing the boot wait time in menu.lst given a longer time  to keyboard wake up...

---

