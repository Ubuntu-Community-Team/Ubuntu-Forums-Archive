---
title: "Fine tuning touchscreen behavior on HP Elitebook..."
date: 2010-08-16
forum: Hardware
---

### Post by demonic_bunny on 2010-08-16
Hey. Installed 10.04 a few weeks back on my Elitebook tablet PC. Everything is working really well, save for the Wacom screen.

It can detect the pen fine, and even has pressure sensitivity working. My only issue right now is that if I rotate the screen to portrait mode (which I have to do manually right now, havent gotten auto rotation down either), the Wacom digitizer doesnt adjust to the change in rotation, so the cursor no longer moves in sync with the pen.

Ive Googled extensivly looking for a solution to this, but, in all honesty, Im a total n00b when it comes to Linux, so what limited info I can find goes way over my head (I gotta find a good crash course on this stuff...)

Anyways, if anyone can point me in the right direction on how I can get this working properly, that'd be great, I got a webcomic to update xD

---

### Post by Favux on 2010-08-16
Hi demonic_bunny,

See the [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1").  Several of the methods should work for you including Magick Rotation.

---

### Post by demonic_bunny on 2010-08-16
> **Favux said:**
> Hi demonic_bunny,

See the [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1").  Several of the methods should work for you including Magick Rotation.

This looks great! Im trying to use Magick Rotation and am getting an error when I run the executable. It says "error get hp_wmi data" Any ideas on what I did wrong? xD

---

### Post by Favux on 2010-08-16
Hi demonic_bunny,

Check if you have hp-wmi installed:
```
modprobe -l | grep hp-wmi
```
If so then see if it is auto-loading:
```
lsmod | grep hp-wmi
```
If not add it to the modules file in /etc.  This is described in:  [http://ubuntuforums.org/showpost.php?p=7738673&postcount=225](http://ubuntuforums.org/showpost.php?p=7738673&postcount=225)

---

### Post by demonic_bunny on 2010-08-22
> **Favux said:**
> Hi demonic_bunny,

Check if you have hp-wmi installed:
```
modprobe -l | grep hp-wmi
```
If so then see if it is auto-loading:
```
lsmod | grep hp-wmi
```
If not add it to the modules file in /etc.  This is described in:  [http://ubuntuforums.org/showpost.php?p=7738673&postcount=225](http://ubuntuforums.org/showpost.php?p=7738673&postcount=225)

I think I need to read up on the basics of Ubuntu, I still don't 100% understand even how to do this. Even the link you provided isnt clear to me. I guess Ill just try setting this up again once I have a better grasp on what I'm talking about.

---

