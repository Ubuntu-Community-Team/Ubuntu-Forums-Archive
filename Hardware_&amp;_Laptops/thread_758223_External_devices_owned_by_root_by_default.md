---
title: "External devices owned by root by default"
date: 2008-04-17
forum: Hardware &amp; Laptops
---

### Post by itix on 2008-04-17
At least that's what I think is the problem. 
I tried the fix in [THIS]("http://ubuntuforums.org/showthread.php?t=278969") post but it did not help.

My iPod, my Western Digital external USB HD and my USB stick has no write permissions for the ordinary *itix* user. I can however access them as root but that's quite irritating. 

This problem stared only recently (together with the underscore problems actually) and since I used the Hardy Beta, I concluded that the problem lay with Hardy and reinstalled my system to Gutsy (since tha was needed anyway). On the 7.04 live disc, and on the pre updated Fiesty I had no write properties either. Has anything happened to my hardware I wonder, because I've soon had three quarters of a problem free year with linux and external devices and this started quite recently.

Anyone else have this problem? I seam to be the only one... :(

---

### Post by Diabolis on 2008-04-18
look at the permissions and the owner of the mount points. You can change them with chmod and chown.

---

### Post by itix on 2008-04-19
I don't mount them manually. I let ubuntu's mount handle that.
Therefor the folders are deleted by mount every time I unmount the drives. That makes the ownership last just one session (at best). I tried a recursive chown on the mount folder prevoiusly, but it didn't help.

The strange thing is also that all three devices (iPod, USB-stick AND WD external HD) suddenly were owned by root without me even sticking them into the computer. I have even repartitioned my External HD since I switched back from Hardy.


Eh...?
I just got an idea as I typed. I inserted my cellular phone into the computer and I HAVE write properties to it. Hardy must have done something to my three other drives that makes them owned by root (ubuntu actually tells me they're owned by root). This is super stange. At least I have narrowed the problem down to that something has happened to my three drives :/

---

### Post by Diabolis on 2008-04-19
Ubuntu won't, at least it shouldn't, modify your devices. Probably if you plugged them into another computer, they'll be just fine. The problem is within the mount points and the way ubuntu is doing it.

Since you don't mount manually, the problem could be in gnome-volume-manager which is the daemon that auto mounts/un-mounts devices.

---

### Post by itix on 2008-04-19
I sort of don't really believe that theory. It wouldn't affect the live CD and pre updated Fiesty Fawn.

---

### Post by Diabolis on 2008-04-19
From my experience, it makes sense if the same happens with the live-cd. I don't know exactly how the live-cd works, but if you use it in a already installed ubuntu box, it kind of blends with it.

I think thats true because you can resintall grub or upgrade packages in the computer while running ubuntu from the disk.

---

### Post by itix on 2008-04-19
Maybe... but how can I get my devices back then. I don't want root to have them all by herself.

...plus, doesn't the live CD completely wipe the system? Are you sure that it might have "merged" with my old system?
I mean, I installed 7.04 and it didn't work before I updated and upgraded to gutsy either. A system wipe would definitely rid all problems i might have my devices that would be stored in the computer. That leaves me with only the devices that might have been changed, right?

---

### Post by Diabolis on 2008-04-19
how about removing and reinstalling gnome-volume-manager?

another thing you can try, if you have spare hard drive space, is too make a ubuntu test installation. See if a clean install solves the problem before messing with the one that you already have.

---

### Post by itix on 2008-04-19
I can always partition the one I have. I'm afraid though that my BIOS can't read external USB devices so that would be a problem. Maybe you can tweak grub to boot off an external drive?

I'll try the volume-manager first

---

### Post by Diabolis on 2008-04-19
you can boot from usb drives with no problem, as long as they are bootable and they have an operating system installed. If grub doesn't detect your drive, reinstall grub so it will add the device to its menu.

---

### Post by itix on 2008-04-19
ouch... I just remembered. I have this rather unusual gfxboot grub that I installed yesterday. Do I have to reinstall that if I want the system to detect my drives??
(plus, I know exactly what I'm going to do. I'm going to try suse 10 with gnome =D )

EDIT: Uh... I can't remove gnome-volume-manager without removing banshee and gnome desktop as well.
TBH, I'd rather NOT do that.

---

### Post by Diabolis on 2008-04-19
gfxgrub is supposed to be the same as grub, so you should be able of reinstalling it just as you do with grub.  

While at grub menu press c then follow this:

```

find /boot/grub/stage1    It will find all the places **from where** you can install grub.
root (hd?,?)              Select **from where** you want to install grub
setup (hd?)               Select the drive **in which** you want to reinstall grub
reboot
```

About gnome.volume-manager, you can try to reinstall it through synaptic manager.

---

### Post by itix on 2008-04-19
But installing it through the synaptic package manager isn't going to help... I mean, it doesn't delete the settings which is the essential part of this operation. I have to do a "complete removal" which require me to remove gnome-desktop and banshee. If I just reinstall the package it'll just affect the binary.

---

### Post by Diabolis on 2008-04-19
mm you are right. Maybe you could play around with it values in gconf-editor, but thats just a wild guess.

Try typing the commands that would remove it and reinstall it **from** the live-cd, riskier but it could work.


I just saw the links in your signature and **emesene** is cool :KS.

---

### Post by itix on 2008-04-20
Emesene is the ****!
I used aMSN for a long time but I hate almost every application written in TCL. As being a TCL application, it crashed on me every other second, the sound broke those every other seconds that it didn't crash completely.
Emesene also has support for Exaile song displaying which is a HUGE plus, and it's written in gtk+ :D

Now before some moderator comes and deletes us both, let's get back to the subject.
How do you use the gconf-editor??

---

### Post by itix on 2008-04-20
Hey!
Nevermind, it solved itself while I slept. I just noticed ;)
A huge thank you for taking your time though. If it wouldn't be misleading for those looking for a fix for their problem, I'd give you a "thanx".

---

### Post by mikesf on 2008-05-28
so what was your solution then? i have the same problem ... usb auto-mounted as root. this is annoying...

---

