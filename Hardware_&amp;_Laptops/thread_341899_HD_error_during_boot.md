---
title: "HD error during boot"
date: 2007-01-19
forum: Hardware &amp; Laptops
---

### Post by Hex_Mandos on 2007-01-19
I was booting Ubuntu today, and it was taking far too long. I assumed that the process had frozen, so I restarted on recovery mode. The boot process wasn't frozen, but it kept giving me hard drive errors like this one:

> ide: failed opcode was: unknown sector
end_request: I/O error, dev hdb, sector 20964825
Buffer I/O error on device hdb2, logical block 0

After a while, I'd be able to log in as root in console mode, and did some stuff (like using text-mode browsers to read the net). 

How do I fix this from text-only mode or a LiveCD?

---

### Post by Nik_Doof on 2007-01-19
> ide: failed opcode was: unknown sector 

With my limited knowledge of kernel ide error messages, it looks like that either its detected your HDD wrong (thinking theres more sectors) or your HDD is on the way out.

---

### Post by Hex_Mandos on 2007-01-19
It was detecting everything perfectly until it died... so I suspect it might be the second option. Isn't there a way to disable only that sector (that is, to mark it as unusable) and keep using the rest?

---

### Post by Hex_Mandos on 2007-01-20
Ok, I'm buying a new HD, but first I'm trying to save as much of my data as possible. Booting from Windows (from a separate HD) I rescued the files I had in my FAT32 partition, so the HD isn't quite dead yet. Is there a way to mount my /home partition (in hdb2) from a LiveCD?

---

### Post by maumau on 2007-01-20
> Is there a way to mount my /home partition (in hdb2) from a LiveCD?

Start up the live

from term
```
sudo mkdir /media/hdb2
```

than
```
sudo mount -t ext3 /dev/hdb2 /media/hdb2
```

ext3 or other fs you need

now you can work in your $HOME in the mounted partition in computer>filesystem>media>hdb2   :cool: 

ciao

---

### Post by Hex_Mandos on 2007-01-20
Thanks. I tried it, and I got an error stating that I was using the wrong fs (which wasn't the case) or a disk error (pretty likely). I decided to do it the other way around, and decided to mount my partitions in Windows via third party software.

Thanks to all those who assisted me.

---

