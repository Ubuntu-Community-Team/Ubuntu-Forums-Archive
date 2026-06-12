---
title: "Changing USB mount point or creating a link to default mountpoint"
date: 2009-09-21
forum: Hardware
---

### Post by hydractive on 2009-09-21
I would like to access the USB memory device (stick, card reader, hard disk or whatever) from within my home directory instead of the default Ubuntu mounting point. I would also have it set up this way for all future users I create but referring to their home directories. What are the pros and cons of the two alternatives a) and b) below, or are there any other option?

a) Changing the mounting point from the default Ubuntu mounting point to a point within the home directory

b) Creating a link in my home directory pointing to the Ubuntu default mounting point (if at all possible, but I guess it is).

Appreciating your ideas

/Per

---

### Post by ajgreeny on 2009-09-21
You can mount the usb disk wherever you want if you add a line to your /etc/fstab file in this pattern:-
```
/dev/sdx# /home/username/mountfolder vfat defaults,user,dmask=027,fmask=137 0 0
```
Without this line the disk will mount automatically to /media/mountfolder.

However, why do you wish to do this in the first place?  Usb disks are mounted as read/write by default, with an icon on the desktop for easy access so I can't quite see why you need to change this.  Perhaps I'm missing something less obvious.

---

### Post by hydractive on 2009-09-25
Working in bash or whatever shell I work in, I find it convinient to access all my working data from within my home directory and being able to refer to files using $HOME.

But I would like to know if there are, for instance, any security related drawbacks for either of the alternatives.

---

