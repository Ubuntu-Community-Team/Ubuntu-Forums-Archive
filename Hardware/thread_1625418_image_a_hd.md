---
title: "image a hd"
date: 2010-11-19
forum: Hardware
---

### Post by COKEDUDE on 2010-11-19
Could I please get recommendations on how to image a hd. What software is best and what methods are best? After a lot of googling these programs are the most talked about that I saw. Is one better than other? Or is one better for certain file systems? I plan on doing this to a ntfs hd. 

partimage, testdisk, Ultimate Boot CD, DeviceImage

---

### Post by stefangr1 on 2010-11-19
> **COKEDUDE said:**
> Could I please get recommendations on how to image a hd. What software is best and what methods are best? After a lot of googling these programs are the most talked about that I saw. Is one better than other? Or is one better for certain file systems? I plan on doing this to a ntfs hd. 

partimage, testdisk, Ultimate Boot CD, DeviceImage

This is actually extremely simple. I believe you can do this with dd, a simple utility that's present by default.

If you run

```
sudo fdisk -l
```

you'll see a listing of your harddisks. Find the one you want to copy, and run

```
dd if=/dev/<hard drive> of=<path to file>bs=512
```

You should be able to mount the resulting file as if it were a real harddisk.

---

### Post by COKEDUDE on 2010-11-22
> **stefangr1 said:**
> This is actually extremely simple. I believe you can do this with dd, a simple utility that's present by default.

If you run

```
sudo fdisk -l
```

you'll see a listing of your harddisks. Find the one you want to copy, and run

```
dd if=/dev/<hard drive> of=<path to file>bs=512
```

You should be able to mount the resulting file as if it were a real harddisk.

Wouldn't it be safer to use a programs I mentioned above? 

Since this is a risky activity wouldn't I need to use sudo?

---

### Post by pawhtiobo on 2010-11-22
I use Norton Ghost, works just fine, simple to use.

Available in any Hiren's Boot CD until 10.7.

see ya...

---

### Post by linux-hack on 2010-11-22
You can use [CloneZilla]("http://clonezilla.org/") is a rely good software for this job.

---

### Post by karthick87 on 2010-11-22
+1 on post 2

---

### Post by COKEDUDE on 2010-11-24
My partition table just disappeared again :(. Is one program better than the other now?

---

### Post by Quackers on 2010-11-24
Oh dear, how did that happen?
If you made a disc image you should be able to restore it I think.

---

### Post by COKEDUDE on 2010-11-24
> **Quackers said:**
> Oh dear, how did that happen?
If you made a disc image you should be able to restore it I think.

The HD is old and about ready to die on me :(.

---

