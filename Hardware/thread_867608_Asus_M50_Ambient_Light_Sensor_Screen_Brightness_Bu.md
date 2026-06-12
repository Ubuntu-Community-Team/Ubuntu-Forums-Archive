---
title: "Asus M50 Ambient Light Sensor Screen Brightness Bug"
date: 2008-07-23
forum: Hardware
---

### Post by 1nxr0x on 2008-07-23
I've tried all of the fixes that I could find on the net, and they either didn't work at all as described, or had to be repeated every time you boot.

Is this an issue that will be addressed in an update or future versions of the *buntu family?

I'm very upset that I can't use *buntu on my new and one and only notebook; this is so frustrating. :(

I've been using Kubuntu, and I've fallen in love with it, but I just can't work with this screen being so dim.

If there is actually ever a real fix for this issue, please post it here in this thread, so that others can easily find it.

There are reports that this bug is effecting other models of notebooks that have an ambient light sensor as well.

Thanks

---

### Post by PaladinOfKaos on 2008-07-23
Anything that needs to be run everytime on boot can be placed in /etc/rc.local. I dunno about future fixes, though.

---

### Post by hotweiss on 2009-01-10
> **1nxr0x said:**
> I've tried all of the fixes that I could find on the net, and they either didn't work at all as described, or had to be repeated every time you boot.

Is this an issue that will be addressed in an update or future versions of the *buntu family?

I'm very upset that I can't use *buntu on my new and one and only notebook; this is so frustrating. :(

I've been using Kubuntu, and I've fallen in love with it, but I just can't work with this screen being so dim.

If there is actually ever a real fix for this issue, please post it here in this thread, so that others can easily find it.

There are reports that this bug is effecting other models of notebooks that have an ambient light sensor as well.

Thanks

A) Open Terminal (Menu->Accessories), and type the following:
sudo nano brightness

B) Now paste the following in the Terminal window:
#!/bin/sh
echo 0 > /sys/devices/platform/asus-laptop/ls_switch

C) Hit Ctrl-O to save and then Ctrl-X to exit.

D) Now we will copy our new shell script to the appropriate directory, make it executable and add the following links by typing the following in Terminal:
sudo mv brightness /etc/init.d
and then
sudo chmod 755 /etc/init.d/brightness
and then
sudo update-rc.d brightness defaults 90

E) Reboot, and you will have regained control of your brightness level.

---

### Post by h4ck3rc1 on 2009-02-02
Confirmed, this worked! Thankyou so much, I have been searching the net for hours after this solution. It even fixed the problem of adjusting the brightness with the Fn+F5 / F6. By the way I'm using an Asus M51V Laptop with Ubuntu 8.10

---

### Post by eliogurt on 2009-06-04
hi, 

how you've configured ubuntu to work with Fn f5/f6??? 

thks
Joan

---

### Post by Darkdelusions on 2009-06-04
Just follow this thread and it will fix all your issues with the light sensor. 


[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=788540](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=788540)

---

### Post by KOTishe on 2009-11-17
And so the easiest way is add brightness applet to taskbar :roll:

Yap, this is not permanet solution, but the easiest way. And after that the brightness can be still regulated.

---

