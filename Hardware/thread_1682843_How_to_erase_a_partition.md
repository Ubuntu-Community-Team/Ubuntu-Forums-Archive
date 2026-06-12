---
title: "How to erase a partition"
date: 2011-02-06
forum: Hardware
---

### Post by EpicMe on 2011-02-06
In the screenshot, there is about 500GB of space on the drive that I cannot access very well. How can I make that space, join the rest of the external drive? 
(Sorry for the obnoxiously large photo!)
[IMG]http://ipic.tk/s/vjv.png[/IMG]

---

### Post by Moozillaaa on 2011-02-06
There's a bunch of ways. Delete the partition, and expand the adjacent partition, for one...

But what exactly do you mean by 'hard to access'? Depending on your hardware (CPU/cache), it will take a few moments to 'map' the drivespace.

---

### Post by ajgreeny on 2011-02-06
I do not really understand what your problem is either.

You have one partition of 1.5TB and 487GB of unallocated space on the disk, so I can see why you say about 500GB is hard to access; it is probably that 487GB.  You simply need to make another partition in that space, or add it to the existing one.    More details please of what you want to do with it.

And in future can you please add screenshots as attachments, not in line, ie use the paperclip icon at the top of the text entry box, and then navigate to your picture.  It is a lot easier to see what you have got and what you are trying to show us if you do that.

---

### Post by EpicMe on 2011-02-06
Sorry for the confusion, but what I am simply asking, is how to make my "500GB" join the rest of the drive without hurting any files. There are no files on the 500GB, just the 1.5TB partition. 

What I mean by hard to access, is that the drive is separated into two on the Ubuntu desktop. 

I see the attachment option now, I will use that from now on.

---

### Post by ajgreeny on 2011-02-06
On the assumption that there is no OS on the disk, boot a Ubuntu live CD and run System > Administration > Gparted, and when you get to the screen with the display of /dev/sda, which is what will show at first, click on the drive dropdown box top right, and there choose /dev/sdc.  

Make sure it is the same disk you show in your picture, which should be obvious from the partition sizes, then ensure the partition is unmounted by right clicking on it.  You can now use the resize button, grab the right hand end and pull it to the far right to make one large partition.

My only uncertainty is about the ease with which you can enlarge an ntfs partition, without re-formatting it at the same time; shrinking is no problem, but enlarging?  I'm not sure, so make certain you have all the files on it safely backed up first somewhere else.

---

### Post by EpicMe on 2011-02-06
I wish I could back up my files, but I do not have a disk big enough to hold everything on this external. This external has been my file storage for a while now, and its were everything else is backed up as well.

---

### Post by ajgreeny on 2011-02-06
In that case just make the unallocated space into another partition, formatted as you wish.

---

### Post by Storm Aiden on 2011-02-07
Maybe this topic shouldn't be under the area of recovery       as its more of a *anti-recovery*       issue. However, if you are getting ready to discard, or give       away an old hard disk, its a good idea to clear the       contents. There are several ways in which you can do this:

[LIST]
[*]You can use the [wipe]("http://abaababa.ouvaton.org/wipe/") utility to thoroughly erase 	  the data on the hard disk. However, this takes a VERY long 	  time (I estimate 775 minutes for a 40GB IDE drive).
[*]You can simply cat from /dev/zero 	  to the hard disk or partition which you want to erase. This 	  is a very quick way to erase the contents of the disk (I've 	  been able to clear a 40GB IDE drive in less than 35 minutes 	  - less than a minute per gigabyte). However, there are those 	  that believe that if one had the right equipment, it might 	  be possible to recover data from a "zeroed" disk by looking 	  at "lingering" magnetic charges left on the media.
[*]You can simply cat from 	  /dev/urandom to the hard disk or 	  partition which you want to erase. This takes roughly 15 	  times longer than using /dev/zero (it 	  took me 532 minutes to clear a 40GB IDE drive using this 	  method).:guitar:):P
[/LIST]

---

### Post by ajgreeny on 2011-02-07
> **Storm Aiden said:**
> Maybe this topic shouldn't be under the area of recovery       as its more of a *anti-recovery*       issue. However, if you are getting ready to discard, or give       away an old hard disk, its a good idea to clear the       contents. There are several ways in which you can do this:

[LIST]
[*]You can use the [wipe]("http://abaababa.ouvaton.org/wipe/") utility to thoroughly erase       the data on the hard disk. However, this takes a VERY long       time (I estimate 775 minutes for a 40GB IDE drive).
[*]You can simply cat from /dev/zero       to the hard disk or partition which you want to erase. This       is a very quick way to erase the contents of the disk (I've       been able to clear a 40GB IDE drive in less than 35 minutes       - less than a minute per gigabyte). However, there are those       that believe that if one had the right equipment, it might       be possible to recover data from a "zeroed" disk by looking       at "lingering" magnetic charges left on the media.
[*]You can simply cat from       /dev/urandom to the hard disk or       partition which you want to erase. This takes roughly 15       times longer than using /dev/zero (it       took me 532 minutes to clear a 40GB IDE drive using this       method).:guitar:):P
[/LIST]

? ? ?

Are you answering a completely different thread?  There is no mention of erasing partitions, the OP simply wants to be able to use the unallocated space.

---

### Post by EpicMe on 2011-02-07
> **Storm Aiden said:**
> Maybe this topic shouldn't be under the area of recovery       as its more of a *anti-recovery*       issue. However, if you are getting ready to discard, or give       away an old hard disk, its a good idea to clear the       contents. There are several ways in which you can do this:

[LIST]
[*]You can use the [wipe]("http://abaababa.ouvaton.org/wipe/") utility to thoroughly erase 	  the data on the hard disk. However, this takes a VERY long 	  time (I estimate 775 minutes for a 40GB IDE drive).
[*]You can simply cat from /dev/zero 	  to the hard disk or partition which you want to erase. This 	  is a very quick way to erase the contents of the disk (I've 	  been able to clear a 40GB IDE drive in less than 35 minutes 	  - less than a minute per gigabyte). However, there are those 	  that believe that if one had the right equipment, it might 	  be possible to recover data from a "zeroed" disk by looking 	  at "lingering" magnetic charges left on the media.
[*]You can simply cat from 	  /dev/urandom to the hard disk or 	  partition which you want to erase. This takes roughly 15 	  times longer than using /dev/zero (it 	  took me 532 minutes to clear a 40GB IDE drive using this 	  method).:guitar:):P
[/LIST]

In no manner whatsoever am I wanting to erase everything on the drive.

---

