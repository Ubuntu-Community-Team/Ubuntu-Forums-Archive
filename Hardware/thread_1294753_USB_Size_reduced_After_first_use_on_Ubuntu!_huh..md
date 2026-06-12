---
title: "USB Size reduced After first use on Ubuntu! huh."
date: 2009-10-18
forum: Hardware
---

### Post by milensinan on 2009-10-18
hi.
it's interesting for me dunno if one of you ever experienced something like this. but ...

Item: Kingston DataTraveler 16GB

After first usage on ubuntu it's size reduced to 750MB. and i absolutely didnt do anything, nothing installed on it of from, or transferred any files in/from..

so, clearly it may be something about Filesystem of it. but what? 

any suggestions? /especially to bring it back to 16GB.

thanks

---

### Post by cybergalvez on 2009-10-18
use gparted to double check what is going on, it should show you what partitions are on the usb and how big they are

---

### Post by milensinan on 2009-10-22
> **cybergalvez said:**
> use gparted to double check what is going on, it should show you what partitions are on the usb and how big they are


ok. i installed gparted and checking usb with it.
normally it had FAT32 fs on it. gparted shows it's ext3 (path dev/sda6). and size is also ok (shows 14
30GB). that's why i couldnt see it on Windows.

here are details:

/dev/sdc1 FAT32 972MB
/dev/sdc2 ext3 9.32GB
unallocated 4.76MB

then i formatted ext3 as FAT32 and now i have two parts both FAT32. then i resized one to replace the all surface. after that i deleted the small FAT32. now what i have:
14.07 FAT32
but: 972MB unallocated

and i cannot use any order on this 'unallocated part' (like formatting or editing).
what should i do next to use the entire disk as FAT32?

thanks

---

### Post by milensinan on 2009-10-22
hm. then resized it again and i think now it replaced 'unallocated' surface with FAT32 and i have one part now (fat32 - 15.02GB).

---

### Post by foobic on 2009-10-23
Is it a cheap Ebay item, by any chance? Lots of those are fake - small flash drives reprogrammed to appear larger. Perhaps it's really only a 1GB drive.

---

### Post by milensinan on 2009-10-28
nope mate, not a cheap one (kingston 16gb - i have two of them).
anyway, i think the problem is solved using 'gparted'.
thanks

---

