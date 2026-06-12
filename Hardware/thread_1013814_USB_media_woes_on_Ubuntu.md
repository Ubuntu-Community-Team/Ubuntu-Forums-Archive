---
title: "USB media woes on Ubuntu"
date: 2008-12-17
forum: Hardware
---

### Post by helbent forleder on 2008-12-17
Hi! I am quoting this from a post that I made 2 weeks ago that went untouched in the *General Support* forum. I seems like a strange problem to me, but there is probably a simple way to deal with it. It's just going to take someone with a better smile and more charm than me to fix it...

I am confused.
I have recently started using Ubuntu eee on my Asus eee 1000H, and for the most part I have to say that it's excellent.
Despite my joy, there's is one sticky matter, that I wouuld love to resolve once and for all! That is that it refuses to automount thumbdrives and SD cards.
If I plug in a thumbdrive the system will tell me that it can't mount it because I have to be SUDO or root or whatever it's called. So, I open gnome-terminal and type:

```
sudo mount /dev/sdb1 /media/thumbdrive

```
This mounts the device and it is readable, but it's not writable...
So in frustration (keep in mind that I know very little about Linux) I tried this command:

```
sudo mount -o owner /dev/sdb1 /media/thumbdrive
```

It had no special effect though.
What makes it writable is to unplug (I never 'unmount') the drive and replug it. Then it pops open Nautilus and I can read and write to my poor hearts content.
What's the deal?
Can someone guide me in making my eee simply automatically mount media that I plug in? I'd like to skip the 2 minute process of making my mounts accessible.
THANKS IN ADVANCE!

---

### Post by MonkeyPaw on 2008-12-17
What I did was run
```
sudo gedit /etc/fstab
```

And added a "#" before this line:

```
/dev/sdc1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

Save and close and USB thumb drives work like a charm!

I think you have to do this when you install via USB, but I could be wrong.

---

### Post by helbent forleder on 2008-12-17
That's just genius... Thanks a million! ):P

---

