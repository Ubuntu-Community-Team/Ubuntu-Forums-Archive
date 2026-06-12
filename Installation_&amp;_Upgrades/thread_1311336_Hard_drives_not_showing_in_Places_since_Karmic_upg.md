---
title: "Hard drives not showing in Places since Karmic upgrade"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by GadiCohen on 2009-11-02
Hi,

I'm writing on behalf of a friend who is waiting for his password reminder; I hope he'll join us here soon :)

He has a 2nd internal hard drive (ntfs) and external usb drive (fat32).  On Jaunty, these would both show up and be mountable on the Places menu.  Since upgrading to Karmic, these don't show up anymore, neither in Places nor in Computer.

The drives and partitions are all good; we can mount them manually with 'mount' no problem.  If we mount them with gnome-mount, they then appear in Places and Computer.  But if we unmount them, they disappear again.

How can we have unmounted partitions show up again in Places, so that we can mount them graphically from there?

Thanks

---

### Post by Remmikins on 2009-11-06
bump

---

### Post by ManiacDan on 2009-11-06
Have them auto-mount on startup:
/etc/fstab <-- the filesystem table file.  Add new auto-mounts here
/root/.cifscredentials  <-- username and password to be used by fstab.  You'll see referernces to it in /etc/fstab
sudo mount -a  <-- re-runs fstab without rebooting

The drives will be detected and placed in places on boot.  Under 9.10, they still prompt for password when you access them for the first time.

-Dan

---

### Post by wanderingarticfox on 2009-11-06
I'm not positive it will work on the external but I have had a lot of success using SUPER GRUB DISC with my dual drive dual boot internal system.

---

### Post by GadiCohen on 2009-11-06
Dan, thanks for the quick reply!

What if we don't want the drives to be auto mounted?

Particarly e.g. the external drive.

If we connect a new drive via USB, it still doesn't show up in places (nor does nautilus pop up with its contents).

Thanks
Gadi

---

### Post by ManiacDan on 2009-11-06
Hmm.  It seems that whatever app is used for auto-mounting drives isn't running.

Go to System->Preferences->Startup Applications.  "Disk Notifications" should be checked.  That's really as far as I can take you.

-Dan

---

### Post by coffeecat on 2009-11-06
> **GadiCohen said:**
> If we connect a new drive via USB, it still doesn't show up in places (nor does nautilus pop up with its contents).

A few people are experiencing a failure of automounting of external USB drives in Karmic. But only a few, so perhaps it's a hardware-related issue. [This thread is an example]("http://ubuntuforums.org/showthread.php?t=1314089"). In my post in that thread I link to another longer one. You'll see that it is fixed for some after an update to udev.

I don't know whether this bug also affects internal drives but, if it does, it could explain your friend's problem.

By the way, the udev update that fixed it for some was a 'proposed' update. Please use the proposed repository with caution. Applying all proposed updates will break your system sooner or later. Other posts in one or the other of those threads seem to suggest that what fixed it for them was a regular udev update. I don't know - but something for you to look at.

---

