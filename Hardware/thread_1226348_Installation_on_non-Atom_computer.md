---
title: "Installation on non-Atom computer"
date: 2009-07-29
forum: Hardware
---

### Post by skewray on 2009-07-29
I have a miniature Via-based computer and I want to install the netbook remix.  I tried installation from a USB memory stick, but it did not work.  I assume that the differences between the Atom and the Via made it gag.  If I installed Xubuntu first, what would I have to do to convert over afterwards?  Or is the situation hopeless?

Brian

---

### Post by mdmarmer on 2009-07-29
What are the specs of your netbook?  What OS does it run now?  What is the make and model?

If you have a hard drive or SD with extra space (8 GB or more total space) you can probably install another OS from Windows or linux from the .iso (using unetbootin or another method).

If your disk is only 4 GB, you can probably add another disk or replace the one you have with a larger disk.

Mike

---

### Post by mikewhatever on 2009-07-29
UNR does not have a special Atom tailored architecture, as a matter of fact, it is the regular 32 bit i386. What you see on the screen is just a different GUI. What was the problem with the installation exactly? You might try, but I really doubt installing Xubuntu would be any different.

---

### Post by skewray on 2009-07-29
The computer is a tiny Advantech industrial computer intended for installation into the front panel of industrial equipment.  I purchased it for the dashboard of my electric car, but I sold the car before installing it.  The computer has some ancient version of SuSE on it now.

Xubuntu essentially is non-functional, because the provided window manager can't deal with the tiny LCD screen.  GUI windows larger than the screen cannot be viewed.  Netbook rocks on netbooks with tiny screens.

I am planning to try something like installing Xubuntu and then copying all of the files in /etc and /home from the Ubuntu netbook.  I am not sure what other bits might differ between the two versions, and which extra pacakges I might need.

Brian

---

### Post by mikewhatever on 2009-07-31
If there is no problem with the installation from the memory stick, as mentioned in the original post, or if you found another way, you can try and install the command line system and then add **ubuntu-netbook-remix** metapackage.

---

### Post by skewray on 2009-08-02
Aha!  Just what I needed to know.

Unfortunately, I ran into another problem.  When I tried to boot up Xubuntu from a USB CDROM (which is how I originally installed SuSE), I got:

ISOLINUX 3.63 Debian-228-07-15  COpyright (C) 1994-2000 H. Peter Anvin
Loading...

and then in just dies.  Clearly the bootloader won't work.  I am not sure if I should try copying the CDROM files to a USB hard disk, or using SuSE to copy the files to a local disk, or maybe use the current Grub install to boot the USB CDROM.  Or something more clever?  Hmmm...

Brian

---

