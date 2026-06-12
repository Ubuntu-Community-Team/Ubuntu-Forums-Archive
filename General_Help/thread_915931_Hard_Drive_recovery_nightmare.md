---
title: "Hard Drive recovery nightmare"
date: 2008-09-10
forum: General Help
---

### Post by dkdkdk on 2008-09-10
Hi all,

I have two SATA 500gb drives. Ubuntu 7.10. No Windows.
I've decided to reinstall the system from scratch, so I've copied all my data to my second drive (sdb), I disconected it, wiped out sda and installed 7.10 again. Connected sdb, and now it Gparted tells me it's unallocated. I also tried "guessing" in gpart - same thing. What could have happened, except for physical failure? I've checked the cables too. Are there other ways of testing/accessing it? 
Thanks!

---

### Post by hyper_ch on 2008-09-10
```

sudo fdisk -l

```

what does that return?

---

### Post by dkdkdk on 2008-09-10
As you can see, "sdb doesn't contain a valid partition table" :(
I did have WinXP on that disk, but after that I did a low level format with MHDD and copied all my files there. What's odd, is that I didn't have write permissions after it was formatted, so I had to change that every now and then when I was copying to it. 


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e9d4f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60045   482311431   83  Linux
/dev/sda2           60046       60801     6072570    5  Extended
/dev/sda5           60046       60801     6072538+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

---

### Post by hyper_ch on 2008-09-10
no clue

did you copy the files from windows on it?

---

### Post by Vivaldi Gloria on 2008-09-10
dkdkdk, 

Does it have any kind of encryption?

---

### Post by dkdkdk on 2008-09-10
> **hyper_ch said:**
> no clue

did you copy the files from windows on it?

no, I copied the files from ubuntu

---

### Post by dkdkdk on 2008-09-10
> **Vivaldi Gloria said:**
> dkdkdk, 

Does it have any kind of encryption?

I have no idea. I'm a newb :)
Is there a way to check? If it was encrypted, is there a different way of accessing it?

---

### Post by Vivaldi Gloria on 2008-09-10
> **dkdkdk said:**
> I have no idea. I'm a newb :)
Is there a way to check? If it was encrypted, is there a different way of accessing it?

If you don't know then I guess it is not encrypted. It doesn't encrypt itself. So my theory goes to trash bin.

---

### Post by bodhi.zazen on 2008-09-10
Yikes ...

Try testdisk , see if it can recover the partition table :

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

testdisk is in the repositories.

---

### Post by dkdkdk on 2008-09-10
> **bodhi.zazen said:**
> Yikes ...

Try testdisk , see if it can recover the partition table :

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

testdisk is in the repositories.

Tried it. Great program btw... but didn't find anything.
That makes no sense! :(

---

### Post by bodhi.zazen on 2008-09-10
> **dkdkdk said:**
> Tried it. Great program btw... but didn't find anything.
That makes no sense! :(

Well, the next option is photorec :

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

If that fails you more then likely need to seek professional assistance and/or your data may be lost :(

---

### Post by dkdkdk on 2008-09-10
> **bodhi.zazen said:**
> Well, the next option is photorec :

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

If that fails you more then likely need to seek professional assistance and/or your data may be lost :(

Photorec **is** working! :guitar:
It's slowly scanning right now and it's actually finding files.
Thank you so much!

---

### Post by hyper_ch on 2008-09-11
still it's curious what happened to it...

---

