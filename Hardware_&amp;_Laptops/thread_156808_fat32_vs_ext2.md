---
title: "fat32 vs ext2"
date: 2006-04-07
forum: Hardware &amp; Laptops
---

### Post by groggyboy on 2006-04-07
so: i have a rather large collection of music and videos on my harddrive.  i am in the process of rearranging it right now, so that kubuntu and windows xp each have their own partition, but i want to put all my songs and such on a third partition.

how should i format it, for best read speed from both operating systems?  how does linux handle fat32?  i know linux can't read data very fast off of NTFS.  how is windows with ext2/3?

---

### Post by heinzbitte on 2006-04-07
I did the same thing before.
I set the third partition as fat32 and it works perfectly with the Windows XP.
For linux I forget how but I had to mount the partition and make it accesible and that was a bit of work but not really too hard.  It seemed to work fine for both windows and linux and I didn't really notice any speed difference between other file systems.

I'm not sure if Windows can read ext2/ext3.  And I've read linux can read NTFS but not very easily or safely.

---

### Post by Sef on 2006-04-07
>  how is windows with ext2/3?

Windows can read ext2, but not ext3.

Whether you choose FAT32 or ext2, is up to you.  Both are used for sharing files between Windows and Linux.

---

### Post by taurus on 2006-04-07
If you want to write to that partition in both Ubuntu and Windows, I suggest you format it as fat32.  Then, mount it somewhere like /personal and turn the write permission on for everybody (since you are the only user on your machine, right?) in /etc/fstab...
```

sudo mkdir /personal  <-- create a mount point
sudo gedit /etc/fstab  <-- to edit it

```
Then, add the following line to the end of /etc/fstab, assuming that /dev/hdb3 is your fat32 partition...
```

/dev/hdb3  /personal  vfat  defaults,umask=0000  0  0

```
Then mount it with
```

sudo mount -a

```

---

### Post by verbalshadow on 2006-04-07
windows can handle both ext2/3 with this [Ext2 IFS for windows]("http://www.fs-driver.org/") ext3 with be mounted as ext2 (i.e. without journaling)

---

### Post by bionnaki on 2006-04-08
keep in mind the file-size limitations with fat32. I believe it does not support/handle any file larger than 3 gigs.

---

### Post by HokeyFry on 2006-04-08
[QUOTE=Sef]Windows can read ext2, but not ext3.[/QUOTE]

Umm... please enlighten me on how to get windows to read an ext2 partition, because I had to download the ext2ifs driver to do that...

unless that is what you are talking about. But then you are wrong because ext2ifs can read ext3 as well. It just reads it as ext2 w/o journalling. Which causes some interesting problems sometimes when you write to it in windows...


And as for the fat32 filesize limit, i think it's 4 gigs.

---

### Post by groggyboy on 2006-04-08
hmmm... so, in the end it's completely up to me?

from what i understand: linux can natively read fat32, but windows needs extra drivers to read ext2.  if no one knows of any performance issues when it comes to linux reading off of a fat32 partition, then i guess that is what i should use.

it's late in my part of the world right now, so i'll sleep on it, and decide on something in the morning.:)

cheers!

groggyboy

(p.s. - anyone know of a website that could break down the pros and cons of various file systems?)

---

### Post by Sef on 2006-04-08
> (p.s. - anyone know of a website that could break down the pros and cons of various file systems?)

Try this site:

[http://en.wikipedia.org/wiki/Comparison_of_file_systems]("http://en.wikipedia.org/wiki/Comparison_of_file_systems")

---

### Post by eriefisher on 2006-04-08
I think there is a partition size limit with Fat32. I don't know off hand what it  is or if it has changed but I could also be wrong here. If true you could just set up multiple Fat32 partitions.

eriefisher

---

