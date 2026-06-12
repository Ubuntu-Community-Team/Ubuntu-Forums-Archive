---
title: "resizing partition using qtparted"
date: 2005-11-04
forum: General Help
---

### Post by eyebrowman92 on 2005-11-04
i cant seem to find out how to use qtprted. i want to resize my current linux partition to fit windows on the disk. can someone walk me through it?

---

### Post by Kyral on 2005-11-04
You want to do it from a LiveCD, 'cause you cannot resize a partition that is currently mounted

---

### Post by eyebrowman92 on 2005-11-04
alright ill switch to the live cd then you can give me further instructions.

---

### Post by eyebrowman92 on 2005-11-04
alright im on the live cd. what now?

---

### Post by az on 2005-11-04
Hmm.  You cannot resize from the beginning.  You can only resize from the end.

You can shrink your partition and then move it elsewhere....

Windows installation will bork your bootloader.  You will have to booth the installer cd after you install windows and chroot into your old linux install, edit your /boot/grub/menu.list to include windows and the run 
sudo grub-install /dev/hda (if it is indeed hds...)

---

### Post by eyebrowman92 on 2005-11-04
um...what...

---

### Post by Samuel on 2005-11-04
isnt it called GParted? thats the one on the ubuntu live CD anyway,
simply start it up, select your root partition and right click it and choose resize from the menu.

what azz was saying is that if you install windows after ubuntu you will no longer beable to boot into ubuntu as windows installation takes over the MBR, however there are plenty of howtos and advice on the subject in the forums once you get to that stage

---

### Post by eyebrowman92 on 2005-11-04
i dont have the 5.10 live cd yet, so i was using the 5.04 live cd. i couldnt find gparted on it so i just gave up. i guess ill wait until december when the cds come.

---

### Post by az on 2005-11-04
Boot the installer or the live cd.

If you are using the installer, boot it and wait until it detects your drives and gets the set of tools (When you get to the partitioner)  CTRL-ALT-F2 to go to a terminal

run
parted /dev/hda
print
resize
(enter the partition number)
(enter the size and stuff)
You then have some free space, so move your partition there (Windows is too egocentric to be anywhere other than at the beginning of your disk)
move
(enter tha partition number)
(enter the area you want it to go)
makepartfs
ntfs
start area
end area
quit
you are done partitioning.  Be sure to update your /etc/fstab and /boot/grub.list to point to the proper partition since it has moved.

Good luck!

---

### Post by az on 2005-11-04
I am not responsable for any data loss resulting from this....


Good luck!

---

### Post by eyebrowman92 on 2005-11-10
alright thanks. i was successful.

---

