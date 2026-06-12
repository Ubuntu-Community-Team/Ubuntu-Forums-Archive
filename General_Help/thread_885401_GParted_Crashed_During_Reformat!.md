---
title: "GParted Crashed During Reformat!"
date: 2008-08-10
forum: General Help
---

### Post by akarimco on 2008-08-10
I was booted into the Live CD environment, and I needed to move my partitions before I installed Ubuntu (which I've done a zillion times), but during the resizing of one partition, the screen turned into a garbled mess and the whole system crashed, totally unresponsive.  Now of course the partition is unrecognizable to GParted... please, oh please tell me there's a way to save my data!

The version of Ubuntu I was using was 8.04.1.

---

### Post by cdtech on 2008-08-10
You could try and boot into the live cd and have a look at "sudo fdisk -l". Maybe Ubuntu can see it, then you could mount and recover. Maybe........

---

### Post by akarimco on 2008-08-10
I tried that, and the partition is there, but I don't actually know how to mount it... I'm still not quite fluent in the command line... in case someone types it out, in my case the partition is /dev/sda2.

---

### Post by cdtech on 2008-08-10
You will need to create a directory under /media:
```
sudo mkdir /media/sda2
```
Then mount:
```
sudo mount /dev/sda2 /media/sda2
```

---

### Post by akarimco on 2008-08-10
OK, I got that far, but it needs me to specify the filesystem, which I did using "-t ntfs", but it's so borked up that it still won't mount it and says that it's not a valid NTFS partition.

---

### Post by GCoffee on 2008-08-10
Ok,

If this was a linux partiton you were resizing, chances are it was either EXT3 or swap, but I have no idea how to put that into the command line..

when it asks you for a filesystem just type in EXT3 or swap, try lowercase and uppercase incase it makes a difference .. thats a lot of cases.. lol

GC.

---

