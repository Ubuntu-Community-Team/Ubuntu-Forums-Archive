---
title: "Reading partitions:  What do I do next?"
date: 2006-02-04
forum: Installation &amp; Upgrades
---

### Post by jimw on 2006-02-04
Okay, I've just got these results:

 df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3             5.3G  2.9G  2.2G  58% /
tmpfs                 253M     0  253M   0% /dev/shm
tmpfs                 253M   13M  240M   5% /lib/modules/2.6.12-10-386/volatile
/dev/hda1             4.9G  3.9G  1.1G  79% /media/windows
/dev/hda6              26G  2.0G   24G   8% /media/hda6

From other posts, I've found out how to make the vfat partiton permanent on each reboot.

The last one, /dev/hda6, is what was the data partiton on my Mandrake.  A bit after I installed Ubuntu, the fellow who introduced me to it showed me how to have that one show up permanently on reboot as well.  Unfortunately, this local fellow is now out of contact, and I've had to reinstall Ubuntu.  

So I know that it's doable, I've done it.  I just don't remember how it's done.  All the suggestions I've seen are based on the notion that the dile will show up in /etc/fstab.  It doesn't.

Every time I have to go into System>Administration>Disks. to redo the thing.

(BTW, is there some way of doing the above through the Terminal?)

Thanks,  

JimW

(I am, of course, pretty much of a noob.)

---

### Post by Pragmatist on 2006-02-04
I'd love to help you, but I'm not sure what your question is.  What exactly are you trying to do?

---

### Post by Herman on 2006-02-04
Yes, we want to help, you will need to find out what filesystem is on your hda6 partition. Is it ext3, or reiserfs? Since you indicated that you know how to mount your FAT32 filesystem, it might be one of those two I guess, otherwise you wouldn't be asking. (Or is it something else?) 
You can make yourself a directory to mount it in in /media if you like:```
sudo mkdir /media/ext3data
```(Presuming ext3data is an appropriate name for it. (You can name it something else if you like).
Then, similar to the way you make your vfat partition remount on each reboot, you can edit /etc/fstab and add another line into it referring to your hda6. The line to add might look something like this:```
/dev/hda6       /media/ext3data    ext3       rw,user        0       2
``` You may substitute the word reiserfs for ext3 if the partition you want to mount is reiserfs.

I'm not certian if you'll need to chmod it or not, but if you try to paste something into it and get a message about not having permission to write to that file then you might want to do:```
sudo chmod -R 777 /media/ext3data
```:-D (Herman)

---

### Post by jimw on 2006-02-04
[QUOTE=Herman]/media/ext3data[/code](Presuming ext3data is an appropriate name for it. (You can name it something else if you like).
Then, similar to the way you make your vfat partition remount on each reboot, you can edit /etc/fstab and add another line into it referring to your hda6. The line to add might look something like this:```
/dev/hda6       /media/ext3data    ext3       rw,user        0       2
``` (Herman)[/QUOTE]

Thanks a lot, Herman.  This was just the information I needed.

Fortunately, I still have the bit of paper on which I wrote down the list of partitions for my hd when I first installed Ubuntu.

Not understanding just what was important about them, I'd sort of ignored the ext3.

Hopefully, I now know better.

I ran through the procedure you suggested, though it wasn't necessary to change the ownership.

I then rebooted, and the file showed up on the desktop when Ubuntu came back up.

Thanks again, and I apologize for not including all the important information in my first posts.

JimW

---

