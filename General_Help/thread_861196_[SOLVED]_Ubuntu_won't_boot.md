---
title: "[SOLVED] Ubuntu won't boot"
date: 2008-07-16
forum: General Help
---

### Post by T2manner on 2008-07-16
I just installed it on my new laptop yesterday and it was running fine.
Then just a few minutes ago i tried to boot it up and it said it couldn't start the X Server and it just gave me a command line.  :(:(

---

### Post by T2manner on 2008-07-16
Come on please!
I NEED to get this fixed.
I've got some important files on Ubuntu.

---

### Post by NikoC on 2008-07-16
Just a quick guess: you have a nvidia graphics card and use the nvidia drivers for that card?
If so, just login via the command line (what you are booting into now).

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup2
sudo nano /etc/X11/xorg.conf

Find the Section "Device" and replace nvidia by nv...

Ctrl + X
Y
Enter

sudo shutdown -r now

This should get you back into your desktop environment...

---

### Post by T2manner on 2008-07-16
No, I've got Intel graphics card.

---

### Post by dracayr on 2008-07-16
probably won't work, but worth a shot: boot up in Safe mode, then select "fix X server"

EDIT: also, post the output of
```
cat /var/log/Xorg.0.log|grep EE
```

EDIT2: before you do anything dangerous, secure your important files by mounting the disk from the liveCD

dracayr

---

### Post by T2manner on 2008-07-16
okay, i'm about to boot into ubuntu

---

### Post by T2manner on 2008-07-16
wait, what doyou mean by booting into live CD

---

### Post by dracayr on 2008-07-16
When you installed Ubuntu, you downloaded the ISO, burnt a CD and then booted from CD didn't you? Insert that CD again and boot it. You can then access your hard drives

dracayr

---

### Post by T2manner on 2008-07-16
OH. Okay good. As long as I get those files off I'll be fine.
I could reinstall Ubuntu if I needed to.


Well I'm on Ubuntu now and it's not letting me access my Ubuntu partition

---

### Post by bodhi.zazen on 2008-07-16
Boot to recovery mode.

Select xfix

reboot  as normal.

---

### Post by T2manner on 2008-07-16
I got it to work when i booted into an older kernel.
but I'm going to try to boot into the newer one and see if it works.
d
EDIT1: Okay somehow it works.  I'm not sure how though. but I'm not complaining :D

---

