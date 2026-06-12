---
title: "Why can't I unmount USB devices?!"
date: 2005-02-02
forum: Hardware &amp; Laptops
---

### Post by ming0 on 2005-02-02
I have trouble unmounting UMS (mass storage) devices. They automount and open in nautilus, but when I close the nautilus window (and make sure that I'm not in any of the devices directories) I get the following error almost every time (but not 100% of the time):

**Unable to unmount selected volume.**
umount: /media/sdb1: device is busy
umount: /media/sdb1: device is busy
Error: umount failed

This is with my camera (sony dsc-u20) and my hdd mp3 player (iRiver H320).

I can't even unmount with the force command:

sudo umount -f /media/sdb1

I get the same error! (the only way I can get umount to work is with the lazy command -l)

Thanks :)

---

### Post by Juergen on 2005-02-02
It seems famd is still looking at the mount.
For me it works to close *all* nautilus windows - then I can umount/'eject' it.

---

### Post by ming0 on 2005-02-02
Ah, that seems to have done the trick! Thanks :)

Should this be posted as a bug? I assume that it would be gnome's fault?

---

### Post by gioyellowsubmarine on 2005-02-02
you're luky. I can't mount my usb key.
can you help me?

---

### Post by ming0 on 2005-02-02
okay, check the basics first: 

Is auto-mount on? This is in Computer>Desktop Prefs.>Removable Storage. It should be on by default.

What happens when you try 'sudo mount -t vfat /dev/sda  /mnt/mpoint' (where mpoint is a directory that you made as root in /mnt/)

you should try the above command with a few variants too /dev/sda1 /dev/sdb /dev/sdb1

I'm sure someone else could give better advice, but that should get you started.

What errors do you get from this? What type of mem key is it? Immediately after plugging it in, can you look at the last few lines of the command 'dmesg'?

Good luck :)

---

### Post by mirtux on 2005-03-06
[QUOTE=ming0]Ah, that seems to have done the trick! Thanks :)

Should this be posted as a bug? I assume that it would be gnome's fault?[/QUOTE]
Hi,
  i'm having the same umounting problems but i'm using KDE.... so no GNOME programs are running... yet no solution!

MC

---

### Post by ming0 on 2005-03-06
I assume you've shut all konq. windows before unmounting, right? 

If I close all the nautilus windows, it generally unmounts properly. This is still an annoying bother--hopefully something can be done about it... 

I haven't done any sort of bug report tho. 

If you want, go ahead and file a report. Let me know if you do or don't--I'll do one when I've got time if you decide not to.

---

### Post by jerome bettis on 2005-03-06
all you have to do is type sudo umount -l <mount point>

the -l is a lazy unmount, and it just does it no matter what.

---

### Post by ming0 on 2005-03-06
[QUOTE=jerome bettis]sudo umount -l <mount point>[/QUOTE]

That is basically the same as pulling the usb cable out of the device without unmounting it first...

---

### Post by mirtux on 2005-03-07
Well.. with this command it seems to work.. but i don't understand what is blocking my device...

---

### Post by landotter on 2005-03-07
Odd, my usb devices unmount perfectly with either a right click on the drive icon, or simply by turning them off. Any related nautilus windows close when I do this. It's rather impressive actually.

Is this a Hoary bug?

---

