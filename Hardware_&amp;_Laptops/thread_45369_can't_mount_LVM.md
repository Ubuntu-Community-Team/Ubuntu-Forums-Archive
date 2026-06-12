---
title: "can't mount LVM"
date: 2005-06-29
forum: Hardware &amp; Laptops
---

### Post by dicklund2 on 2005-06-29
I reinstalled ubuntu becuse of a crasch and now I cant mount my old LVM
Old was created wiht ubuntu 4, now I have 5. But I dont think thats the problem...

pvdisplay and lvdisplay shows what I think is right. 

but when I try to mount it says something about wrong fs type, bad option, bad superblock on LVM or other error.

then i found a "Moving a volume group to another system" how-to and tried that.

and all works until mount. then I get the message:
mount: /dev/LVM is no block unit   (freely translated from swedish "är ingen blockenhet")  ](*,)

hope you can figure out the right translation for that...     cant find anything when i search, sorry...


How can I check if the filesystem on LVM is ok? thats a good start :)
-----------------------------------
Edit:
just tried to restart, and i fails suspect diskcrasch (fsck gives some inod error part of orphaned....??  hda3)


hda1 /boot 
hda3 the install 
hda6  LVM  starts
hdc1  LVM continus

As you can see my LVM spans over both discs and i start to guess that the disk is BAD....

when I try fsck /dev/hda6 or hdc1 I get "The superblock could not be read....."  Is this becouse of LVM or becouse of crasch?

How can I fix it so I can recover data and remove bad(?) disk ?

---

### Post by deBaas on 2005-06-29
From my experieces you'll need the lvm files in /etc/ to get back your files. I had to find out the hard way; 2x200GB.

---

