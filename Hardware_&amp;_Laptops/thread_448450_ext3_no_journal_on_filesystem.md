---
title: "ext3: no journal on filesystem"
date: 2007-05-19
forum: Hardware &amp; Laptops
---

### Post by amagi on 2007-05-19
Hi there,

I have a BIG BIG problem and I am afraid I made it even bigger!!!!

I have an external 250Gb USB harddisk. I have used this disk without problems on edgy eft for a long time. Last week I used it on feisty and suddenly when i wanted to open directories it started showing '0 files present'!!! I disconnected the drive in the hope that this was just a glitch.
After trying to connect it again it would not mount anymore. I tried it on my 'old' edgy and it also gave the same error:

ext3: no journal on filesystem

I then tried to use fsck.ext3 to recover the filesystem and answered yes on all questions (I have done all this on edgy as I did not trust feisty anymore). In the end the harddisk mounts again but here is where my BIG problem starts. Some of the folders keep saying they have 0 files in them and a few folders just simply dissappeared. It almost looks as if the devil itself was responsible for this because there was a lot of stuff on the disk which didn't matter that much but one folder was important, all my photos which were stored by f-spot. The whole 2006 directory is just gone so I lost all my photos.

Now off course the big question, please please please, if anybody can give my anything I can try to recover that folder you will make my day (or entire year for that matter!!!).

Any help, tip, suggestion is very much appreciated (except the advice of making a backup because I know I was stupid not to do so, so you do not need to rub it into my face :(.

Morten

---

### Post by kidders on 2007-05-20
> **amagi said:**
> Any help, tip, suggestion is very much appreciated (except the advice of making a backup because I know I was stupid not to do so, so you do not need to rub it into my face :(.Seriously... making a backup now is a smart idea. That way, you can play around as much as you like, experiment with potentially destructive recovery tools, and undo anything that makes things worse.

If this happened to me, and the lost data were very important, the first thing I would do is take a byte-for-byte copy of the damaged filesystem, and run recovery operations on *that*... not the original hard disk.

In terms of the data recovery itself, images tend to work very well with metastructure-based recoveries (which are non-destructive). Once you have your backup, there's no reason not to try pretty much anything though.

[COLOR=Silver][[SIZE=1]*[UAResolved]*[/SIZE]]("http://ubuntuforums.org/showthread.php?t=377083")[/COLOR]

---

### Post by PCFascist on 2007-08-22
Just in case someone else has this problem... I was able to remount my device after running
```
tune2fs -j /dev/sdb1
```

---

### Post by mkljun on 2008-02-28
Thx PCFascist.

I had the same issue. I created a new partition with gparted and put in fstab and I got the same error. Strangely enough I created an ext3 partition but ended up with ext2. I either missed something in the process or missed something in the process :).
```

$ sudo vol_id -u /dev/sda6
6115107b-1062-4b48-8247-29b6f6b83dfc
```

I added a line in fstab:
```
$ gksudo gedit /etc/fstab

UUID=6115107b-1062-4b48-8247-29b6f6b83dfc /media/data     ext3    defaults,rw,nosuid,nodev 0       1

```
```
$ sudo mount -a
bla bla error bla bla ....
$ dmesg | tail
[  105.524000] ext3: No journal on filesystem on sda6
```

I didn't even check if sda6 has ext2 or ext3 on it. I was sure it had ext3. After finding your post here I double checked and it really had ext2 partition. tune2fs solved the problem.

lp mk

---

### Post by Anjue on 2008-07-08
Thanks PCFascist. Your solution is work for me.

---

