---
title: "USB-HDD is suddenly, magically, even, read only."
date: 2010-02-27
forum: Hardware
---

### Post by UraniumOrchid on 2010-02-27
Hi there Ubunters --

I'm actually from the dark side, currently running Fedora 12 on my laptop (but strongly, very strongly considering a conversion these days). Since I find Ubuntu people far more willing to help idiots such as myself with strange problems I thought I would post my question here.

I'm planning on dual booting my laptop, and so, have set about backuping my files since there is about a 90 percent chance I'm going to break something.

Anyways, when I plugged in my fairly aged USB-HDD I got a nice little error message telling me 'one or more disks are failing' but after a lot of research found that in all probability this is just moodiness on the part of the HDD checker. Fine.

I begin copying my files, and of course, there are a lot of them. At first everything seems to be moving fine and so I walk away, go to class get some food, come back and find that there was some error in the copying. I accept the error, and decide I'll just recopy that folder (pictures, if that's important). Of course no sooner does the file copying process halt then suddenly my HDD has locked me out, read only apparently. Only about half of my files copied successfully.

I've tried CHMODing, I've tried kicking it about in Nautilus, I've tried asking very nice, but to no avail, nothing will return my drive to read-write. I can't finish my backup, and therefore can't move forward with my dual boot until this bloody thing starts writing again.

Anyone have any bright ideas?

```
ls -l /media/USB-HDD/
total 107424
-rwxr-xr-x  1 Kae Kae 10308608 2006-11-15 11:21 1576 Calgary.doc
-rwxr-xr-x  1 Kae Kae   971264 2006-11-14 15:39 9013 Cochrane.doc
drwx------  6 Kae Kae    32768 2010-02-23 15:18 Caitlin
drwx------ 21 Kae Kae    32768 2008-08-31 00:09 Daniel
-rwxr-xr-x  1 Kae Kae 14676992 2006-11-15 12:52 Edmonton1572.doc
drwx------  0 Kae Kae    32768 2008-12-02 21:06 FOUND.000
drwx------  2 Kae Kae    32768 2005-11-04 13:58 PCF
drwx------  0 Kae Kae    32768 2006-09-27 08:46 RCSS
drwx------  2 Kae Kae    32768 2008-07-27 18:05 $RECYCLE.BIN
drwx------  3 Kae Kae    32768 2006-09-25 15:10 Recycled
-rwxr-xr-x  1 Kae Kae  1178112 2006-11-14 15:18 Regina 1584.doc
-rwxr-xr-x  1 Kae Kae 12980224 2006-11-15 11:04 Stony Plain ED 1573.doc
drwx------ 11 Kae Kae    32768 2005-11-04 13:58 System Volume Information
drwx------ 16 Kae Kae    32768 2006-09-18 17:20 temp
```

---

### Post by TitanusEramius on 2010-02-28
It sure sounds strange, I can't say I've tried something similar, but have you made a line for the ext-hdd in fstab?

One of my lines looks like this:
```
UUID=556C3CF83FBC78EC    /media/film           ntfs-3g rw,async,user,exec,locale=da_DK.UTF-8         0 0
```

Since I dualboot with Windows, this drive is formatted in ntfs, should you actually try it you have to change that and the locals to what you are using. For reference you can read:
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

I hopes this helps

---

### Post by UraniumOrchid on 2010-02-28
I'll try that as soon as I get home -- and edit this post with my results.

Thank you for your speedy reply. Fingers crossed!

---

### Post by UraniumOrchid on 2010-03-12
Okay, in my fstab my external hard drive isn't even showing up...

I actually have no /media/ directories at all...

---

### Post by TitanusEramius on 2010-03-13
Well neither thing should be a problem, but some of these suggestions might not work on your system. Since you don't have a /media to mount in you could use your home-dir or maybe /mnt if your system have that dir, but it's not that important since you can mount to any empty folder you like, even a folder you creates on the desktop itself.

At least on Ubuntu a external harddisk don't need an entry in fstab (the system just automounts it with default settings), but if you make one for it you can control things like mount-point and more important what users and what groups should have access to it. 

So as an example one could do this:
First make a dir we can mount in, and in this example I placed it in /home/username 
```
mkdir /home/username/extmnt
```(extmnt being the name of the folder in this example)

Then you need the UUID or the label from the external harddisk and blkid is used to find those
```
sudo blkid
```Sudo might not work for you, but blkid needs a administrators password to run.

And when you have found the proper UUID (or label) then open fstab and add a line like this in the bottom:

UUID=4cc71ab2-7d34-42da-b9cd-935956793d06   /home/username/extmnt   ext4   defaults   0 0

Like I mentioned you can use label instead of UUID, just start the line like this "LABEL=exthdd" instead. There is also a third way to identify a harddisk in fstab, but UUID or LABEL is best. In this example the UUID is from a ext4 harddisk, if you have it formatted with NTFS or something else the UUID will be very different. The next thing is /home/username/extmnt witch tells the system where to mount, and here you have to point it towards the dir you made before. ext4 tells what filesystem it is and is it NTFS you have it's ntfs-3g instead (and ext3 for that).

The next thing is telling the system what settings the drive should be mounted with, and I would start with defaults to see if it's working with that and if not you should read the link I provided in the first post about the extra settings you can add here (it will be settings like user). If you need to add two or more settings here you have to separate them with a comma and no spacing (like "defaults,user"). The two zeros in the end tells the system that chkdsk is not needed on this disk.

After all this you just type "sudo umount -a" and then "sudo mount -a" where the first command will unmount all harddrive not in use, and the second command will mount all harddrives there have a entry in fstab.

I don't hope I confused you with all this, but I hope it will point you in the right way :)

---

