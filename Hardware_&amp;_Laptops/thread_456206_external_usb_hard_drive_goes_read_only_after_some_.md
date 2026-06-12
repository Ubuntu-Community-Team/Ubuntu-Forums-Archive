---
title: "external usb hard drive goes read only after some time"
date: 2007-05-27
forum: Hardware &amp; Laptops
---

### Post by rockfishenator on 2007-05-27
I have a 80G external USB hard drive that when pluggedd in to my laptop(I am running Feisty Fawn) goes to read only after about an hour. Any ideas on how to fix this? It is plugged in 90%of the time.

---

### Post by optimarcus_prime on 2007-10-22
I am actually having the same issue here.  I have a Seagate 250GB external USB hard drive.  When I boot up the computer, it seems to be working fine, and before I reformatted my primary hard drive with 7.10, it was working fine.  However, now, after a certain amount of time, the hard drive becomes unusable.
If I try to access it through Nautilus I get:
> Sorry, couldn't display all the contents of "disk".
If I try to access the disk through the command line I get:
> marcus@mothra:~$ ls /media/disk
ls: reading directory /media/disk: Input/output error

The drive is connected to the computer through a USB hub, if that makes any difference.  I tried reformatting the drive with the command:
```
mke2fs -j -m 0 /dev/sdb1
```
...but I get the same result.  I've never messed around with fstab or mtab, but I get the feeling that they might be the culprit.  Any ideas?

---

### Post by optimarcus_prime on 2007-10-22
Bump?

---

### Post by iansyngin on 2007-11-16
experiencing the exact same problem.
What i have to do as a work around is this.

Unmount the USB Hard Drive. Should be something similiar to do below:
sdb1 is my usb device

```
[FONT=Courier New] sudo umount /dev/sdb1 [/FONT]
```then run a file system check on the disk while it's unmounted.

```
 sudo fsck /dev/sdb1 
```

Mine constantly reports an error with bad block or something.
then we can simply remount the devise 
I think the folder Disk need to be created before it can be mounted there.

```
 sudo mount /dev/sdb1 ~/Desktop/Disk 
```


Maybe someone could suggest an alternative to this. Perhaps a way of mounting that means we don't have to create that folder.

---

### Post by kernel tom on 2008-01-25
I also have this problem with a Seagate external

Mines formatted as EXT3

It seems to do this after it goes into "sleep mode".  My guess is that Ubuntu believes that something has happened to the device (like a power failure or yanking out the usb chord) and makes the drive read only to protect data.

I would guess a solution would be to have a cron job 'touch' a file every so often to not allow the drive to go into sleep mode, but there has to be a better way

Does anyone know how to fix this?  (I kinda like the feature cause I network share this drive, but I also have a "drop" partition thats writeable, but when this happens i need to umount/mount it again)

-kt

---

### Post by kernel tom on 2008-01-26
check this out 

[http://ubuntuforums.org/showthread.php?t=679228](http://ubuntuforums.org/showthread.php?t=679228)

---

### Post by iansyngin on 2008-02-06
Cheers Kernel for the Link. I was having problems from day one with my external hard drive going read only after about 25 minutes and was becoming a major pain in the @ss. Anyway the link you provided solded the problem. Do you know if this fix will be included in future builds or should i just record this step for future builds?

syngin

---

### Post by kernel tom on 2008-02-07
I would write this down somewhere, or keep the steps in a text file somewhere on your computer so you won't forget it...

I don't think this is a 'problem' as far as linux/ubuntu is concerned, its more of a built in safety feature, as well as a power saving feature.  There may be other ways to work around this problem, like allowing the drive to be 'woken up' as rw by the os... Until then tho, this seems to be the way to go.

I would guess if enough ppl complain about it, developers will make this feature more easily manageable.

-kt

---

