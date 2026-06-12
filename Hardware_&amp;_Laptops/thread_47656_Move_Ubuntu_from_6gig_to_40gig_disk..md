---
title: "Move Ubuntu from 6gig to 40gig disk."
date: 2005-07-09
forum: Hardware &amp; Laptops
---

### Post by fipeso on 2005-07-09
Hello,

I have a small linux server on a 6GB disk. 

I want to move the working Ubuntu system from the 6GB disk, to a new 40GGB disk, with minimum effort.

I tried to use ghost, but when I try to boot from the ghosted 40GB, all I get is a text "Grub" on the screen.

Please help

---

### Post by Firetech on 2005-07-09
Ghost doesn't work very well with grub, at least not with the EXT3 file system.

I did this some weeks ago, and I did something like this:
Boot the Installer CD and start installing a "server" system (type "server" in the boot menu) on the new drive.
When the install is finished, boot into a Live CD and mount both drives to one folder each (not inside eachother!) using the command "sudo mount /dev/hd[something]  /existing/folder". (E.G. "sudo mount /dev/hda1 /old" and "sudo mount /dev/hdb1 /new")
Clear the new drive (The installation was just to fix all the partitions and the boot sector... There are shorter ways, but those are a little bit harder, atleast to explain...)
Then copy the files from the old drive to the new drive using the command "sudo cp -R --preserve=all,links /mount/point/of/OLD/drive/* /mount/point/of/NEW/drive/".

You can also do the mounting and copying when you're running from the old drive, but I recommend copying the files from a system not using any of the files. Do NOT, I repeat, NOT do it when ruinning from the new drive as it won't work becuase of the clearing of it.

---

### Post by fipeso on 2005-07-09
Thanks, I try this.

I dont fully understand it but I give it a try :)

---

### Post by Firetech on 2005-07-09
If you get stuck somewhere, don't hesitate to ask... :)

---

### Post by fipeso on 2005-07-09
Ok,
I have now installed the Ubuntu server, connected both drivers to the PC and booted up with KNOPIX.

Knopix has allready mounted hda1 and hdb1. hdb1 is the old drive.

How do I clear the drive? I changed the state from properties to writable and removed a "read only" selection from hda1/properties/device, but still I get an acces denied, when I try to delete files from the new disk.

---

### Post by fipeso on 2005-07-10
I booted knopix to level 2, and mounted the disks as you told me.
Now I am able to rm -r the directories from the new disk :)

Im in the proces of copying now. Boy is an old 400MHz slow :)

I hope this work.

Thank you very much.

---

### Post by fipeso on 2005-07-10
It worked perfectly !

Thank You again :)

---

### Post by Firetech on 2005-07-11
Knoppix in level 2 is the solution to everything ;) It has saved me many times.
I'm glad it worked out for you... There is at least one shorter way to do it, but that one is a bit more complicated to explain, as it requires some chroot-ing...

---

