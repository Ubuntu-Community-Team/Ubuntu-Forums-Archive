---
title: "How to mount floppy and hard drive??"
date: 2005-03-10
forum: Hardware &amp; Laptops
---

### Post by howard on 2005-03-10
I'm running the new Ubuntu 5.04 Preview Live CD and would like to know how to mount my computer's internal hard drive [IDE]  and floppy drive.
Thanks.

---

### Post by lorap on 2005-03-10
hi buddy!
if you need to mount something do the next things:
i.create any directory in your director:

sudo mkdir /home/yourusername/newdirectory

ii.i.sudo mount /dev/hda0 /home/yourusername/newdirectory -t ntfs -o umask=000 

(that'll mount a hard drive,but not permanently until you unmount it or restart the pc,you can write "vfat" instead of "ntfs" if you've fat32 and instead of "hda0" you have to use "hda1" or other if your windows directory isn't the first drive)

ii.ii.sudo mount /dev/fd0 /home/yourusername/newdirectory

(this'll mount your floppy)

iii.to unmount devices:

iii.i.sudo unmount /dev/hda0 -f

(for the hard drive)

iii.ii.sudo umount /dev/fd0 -f

(for a floppy)

have a nice day friend!
pavel

---

### Post by howard on 2005-03-10
Thanks, Pavel.  Seems simple enough.  I wonder why the developers didn't just let Ubuntu detect the HDD and floppy and put an icon for each on the desktop.
Regards,
Howard

---

### Post by lorap on 2005-03-11
hi Howard!
there's a possibility to mount all devices you need by adding them to "/etc/fstab",
but i don't remember the settings,that's why didn't write you about it anything.
you can post a question so someone who knows hot to do that will tell you what you'd  do.
the reason they didn't add them automaticly,i think,is that when device's mounted you'd send it acknoledge every nano seconds what slows down the work.
i'm very happy could help someone!
pavel

---

