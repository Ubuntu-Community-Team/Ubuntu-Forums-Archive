---
title: "Xubuntu won't boot after installing SATA PCI card + SATA HDD"
date: 2008-07-26
forum: Hardware
---

### Post by jsguzek on 2008-07-26
Ok, I've been searching online for hours with no luck.  Here is my problem.  I have a Xubuntu system that has been running nicely as a file server for some time on a single IDE HDD.  I wanted to add some serious storage capacity, so I got a SATA PCI card and HDD.  The probelm is that when the drive is attached to the card, the system won't boot.  

Specifically, I get through the grub screen, then I see "starting up" followed by "loading" followed by the Xbuntu splash screen.  After a few seconds of the bar bouncing back and forth, the screen goes blank, except for a flashing cursor at the top left.  

Now, if I shut down and unplug the drive, then power up, I am fine.  Once I am in Xubuntu, I can plug the drive in, see it, mount it, etc.  So I know the card and drive are working.  In fact, I can always unplug the drive when rebooting and plug back in once booted as a very cumbersome work-around, but surely there is a better way.

Here are some system details:
Celeron 1.2 Ghz
512 MB RAM
80GB IDE drive as primary
750GB SATA drive (the one that is causing the problem)
Rosewill RC-209-EX SATA PCI card (Silicon Image Sil 3114 controller)

Any advice would be appreciated...

---

### Post by markbuntu on 2008-07-26
I just put a SIIG SATA PCI card in my machine and found I had to change the slot it was in to get it to work. It has its own bios and shows at boot and lists the drive attached to it. But it did not mess with my system, it just didn't show up.

I don't know what chip it has in it and I am running Ubuntu Hardy.

It is possible that Xubuntu is trying to read the drive and crashing, Is this drive formatted?

---

### Post by jsguzek on 2008-07-26
Thanks for the reply, but I just got this problem fixed by a friend of mine.  It turns out that there was a program running called "uswsusp" that was running during start-up that was getting the drives confused and preventing the system from recognizing the swap partition.  Turns out this program is only needed for laptops (has something to do with using standby), so I just removed it and all is well with the world now.

---

### Post by markbuntu on 2008-07-26
Excellent. Now we know that your card also works.

---

### Post by 4ks on 2009-05-21
I have this same card (rc-209 SiL 3114), as well as a rc-200 SiL 0680 card. The both work in windows, but in ubuntu it shows 'usb mass storage device' in computer, when i try to open it, it says it cant be mounted, I havent installed any drivers for this, don't know how... 

Is there any help for me?

Also, sorry for bringing up an old thread.

---

### Post by ScaryBob on 2009-07-06
I have similar issues. I have never been able to get Ubuntu installed correctly with a Sil 3114 card present. Ubuntu gets confused about which drive should be primary and where to install the boot loader and which drive it should boot from. It's a common problem with other Linuxes as well.

p.s. - Sorry for the "me too" post but I haven't yet solved this issue. My solution was to switch to another distro that installs correctly.

---

