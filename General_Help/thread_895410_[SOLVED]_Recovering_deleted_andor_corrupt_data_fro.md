---
title: "[SOLVED] Recovering deleted and/or corrupt data from NTFS?"
date: 2008-08-20
forum: General Help
---

### Post by phantomjoker on 2008-08-20
Hi

I recently discovered a folder containing all my work has been delete.

The folder was on my external (NTFS) - but everthing else is untouched, including everthing else on that external.

I have been trying everything in a desperate attempt to recover anything...

If anyone has any ideas of what to try - i literally mean anything - im desperate at the moment. 

So far i have tried 

magicrescue - can't understand it enough to get it working
undeleteplus - through wine - doesn't do what i need
.trash - searched for anything similar - nothing

[Code:]
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sdb1[/code] - did not work

testdisk - recovered some plain text and .doc files - all corrupt


So i'm stuck - really appreciate any help - im going crazy

cheers

---

### Post by ozorba on 2008-08-20
Try this:

[http://ubuntu-my-choice.blogspot.com/2008/08/use-ubuntu-live-cd-to-backup-files-from.html](http://ubuntu-my-choice.blogspot.com/2008/08/use-ubuntu-live-cd-to-backup-files-from.html)

---

### Post by caljohnsmith on 2008-08-20
Try [Herman's web page on file recovery]("http://www.users.bigpond.net.au/hermanzone/p21.html"), especially the part about using "photorec". I think that will help you recover more of your files.

---

### Post by phantomjoker on 2008-08-20
im using it - and its working, but i have no space, how do i access my second partition, it should be visable, but i dont know how to get to it...??

---

### Post by colobix on 2008-08-20
Download PhotoRec.
It will let you recover your files on other places then the one u deleted them from.

---

### Post by caljohnsmith on 2008-08-20
> **phantomjoker said:**
> im using it - and its working, but i have no space, how do i access my second partition, it should be visable, but i dont know how to get to it...??
You'll need to be specific; when you say you "have no space", do you mean the entire HDD is full, or just a certain partition? And which is your second partition--Windows, Ubuntu, or something else? It would be helpful if you could post the output of:
```
sudo fdisk -lu
```

---

### Post by phantomjoker on 2008-08-20
this part is solved - but im still trying to recover data 

my external has no partition table!!!! WHAT?

> Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1b93a530

Disk /dev/sdb doesn't contain a valid partition table


---

### Post by aysiu on 2008-08-20
If you have already installed *testdisk*, you can use Photorec to recover the files:
[http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-iii-deleted-files/](http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-iii-deleted-files/)

---

### Post by phantomjoker on 2008-08-21
I have started using photorec and it is pulling in files - i have another thread running with newer problems so i will call this once solved (even though it is not)

cheers guys

---

