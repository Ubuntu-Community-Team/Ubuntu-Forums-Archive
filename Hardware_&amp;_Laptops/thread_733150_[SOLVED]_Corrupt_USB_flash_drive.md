---
title: "[SOLVED] Corrupt USB flash drive"
date: 2008-03-23
forum: Hardware &amp; Laptops
---

### Post by durand on 2008-03-23
I have a strange problem here. I'm not sure how related to ubuntu this is or whether it's a physical problem but my usb flash drive (corsair voyager 1gb) has suddenly stopped working.

fdisk -l gives me this:

Opened disk read-only - you have no permission to write

dmesg gives me lots of errors:

> 
[13319.613052] sd 6:0:0:0: [sdb] Sense Key : Medium Error [current] 
[13319.613059] sd 6:0:0:0: [sdb] Add. Sense: Unrecovered read error
[13319.613067] end_request: I/O error, dev sdb, sector 32
[13319.613073] Buffer I/O error on device sdb, logical block 4
[13319.615534] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[13319.615540] sd 6:0:0:0: [sdb] Sense Key : Medium Error [current] 
[13319.615547] sd 6:0:0:0: [sdb] Add. Sense: Unrecovered read error
[13319.615554] end_request: I/O error, dev sdb, sector 40
[13319.615559] Buffer I/O error on device sdb, logical block 5
[13319.618033] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[13319.618039] sd 6:0:0:0: [sdb] Sense Key : Medium Error [current] 
[13319.618046] sd 6:0:0:0: [sdb] Add. Sense: Unrecovered read error
[13319.618052] end_request: I/O error, dev sdb, sector 8


gparted doesn't detect the disk and nautilus gives this error:

Unable to read /dev/sdb:
Can't mount file

With cfdisk, I get this error:
> 
Opened disk read-only - you have no permission to write

All this was done with su privelegdes.
My fstab doesn't have anything related to sdb.


Can anyone help me here? I've had this drive for about 2 years now and haven't had any problems. It's of a good built quality and I can't think of anything that I may have done that could cause this.

Thanks in advance.

---

### Post by fela on 2008-03-23
when did the problems start? did you do anything to it, e.g. reformat or something?

---

### Post by durand on 2008-03-23
They started last week and I don't think I even touched it. I put a few files on there for school but it just randomly stopped working. Worked one day, not the next. First found the problem when trying to access it on the school's windows laptops but I don't see any link.

---

### Post by fela on 2008-03-23
I'm a bit of a n00b in this respect, but i'll give my two pence. i would suggest first that you reformat your drive. To do so, first plugin the drive into a PC running ubuntu. 
Then, ```
sudo fdisk -l
``` hopefully you will see your device (if it recognizes it). Look for the one with the same size as your disk (e.g. a 1gb stick will be 1024MB or similar), and that will have a label near it, that says /dev/sdx, x being a letter, i will assume in this howto that it's /dev/sdb, but if it's not then [COLOR="Red"]REMEMBER TO REPLACE THE LETTER 'b' WITH THE RIGHT ONE, OR ELSE YOU COULD EASILY BRICK YOUR SYSTEM[/COLOR]. 
Ok, now run ```
sudo mkfs -t vfat /dev/sdb1
```

wait for the prompt to come up again, and your done. Now run ```
sudo mkdir /mnt/usbstick && sudo mount -t vfat /dev/sdb1 /mnt/usbstick
```

tell me the output if it doesn't work :guitar:

---

### Post by durand on 2008-03-23
Sorry, but the first command is the problem.

> fdisk -l gives me this:

Opened disk read-only - you have no permission to write
as I said above.

It displays my hard drive contents correctly, just give the error for my flash drive

---

### Post by durand on 2008-03-23
Ok, now this is seriously weird.....I just plugged it in and it seems to work right...

Any idea why? It hasn't been working for a week on ubuntu and windows and now it suddenly works....

Thanks a lot for your time. Hopefully, it will work from now on.

---

### Post by fela on 2008-03-23
well if it ain't broken, don't fix it...problem solved :)

---

### Post by durand on 2008-03-23
Thanks!

---

