---
title: "wubi 9.04 stopps"
date: 2009-08-26
forum: Installation &amp; Upgrades
---

### Post by ottosykora on 2009-08-26
I have now tried to make a wubi installation of 9.04.

All went fine, but when it come to creating the disks, the wubi installer hangs for ever. Process pyrun.exe takes 100% of the CPU power for ever, nothing happens any more.

Host system is XP, sp3, 22gb free on the partition, tried number of times, different sizes of wubi installation but no cure.

I have done wubi install on other computers , versions 8.10, all went fine then.

Is there some problem with the wubi of 9.04 version?

---

### Post by inobe on 2009-08-26
it may be trying to suspend to disk or power save may be trying to kick in, move the mouse every few minutes to prevent it.

---

### Post by ottosykora on 2009-08-26
negative
tried, but does not help

there is no suspend or any other temp shut down or screen saver etc existing on this PC.

It is running all the time full. After it creates folder, changes boot.ini etc, it starts with creating virtual disks. The bar then goes to abt 80% and remains there for ever. CPU load goes to 100% and stays there.

Tried to get other copy of the wubi from the website, no cure.

The host is nothing special, just XP desktop , on exactly the same one I did similar install with wubi 8.10 some time ago.

Are there any problems known to wubi 9x?

---

### Post by inobe on 2009-08-26
none that i am aware of, i recently installed on two machines without error.


a shot in the dark' have you defragged the disk, also how much space did you assign and is it on an ntfs partition ?

edit: you can download the ubuntu .iso and burn it to a cd' wubi will run from that, if you don't have a cd' you can download magic iso and mount the ubuntu iso as a virtual cd.

---

### Post by ottosykora on 2009-08-26
ok I tried to assign 5, 7, 10 gb, all failed.

On the disk nothing is there except the ubuntu iso and one folder with some small virtual machine. Defragged when used last time, but there nothing to defrag in fact, 22gb free space abt.

None of my partitions are ntfs, I use fat32 in general on all machines.

On the similar machine I was installing 8.10 wubi few moths ago, all went fine, also there all in fat32. So if it needs no to be ntfs...?? BUt why? the disks are done on fat in smaller portions on my other machine.

---

### Post by P4man on 2009-08-26
I dont have any real experience with wubi, but  you are using FAT32. Maybe that IS the problem after all. Fat is limited to 4GB files. I think wubi makes a single large file on the host's drive that it mounts as filesystem. It wouldnt be able to make a file > 4GB on a FAT32 partition.

---

### Post by inobe on 2009-08-26
here is the docs [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

see if there is anything resembling what your experiencing.


note: if the system suffered from a hard reboot this will happen, you must be able to restart clean in order to use wubi.

---

### Post by ottosykora on 2009-08-26
tzried to read on the wubi site, could not find anything abt ntfs etc.

On my other installations, all done with 8.10 or 8.04 wubi, there is not one single disk file. The disks are rather created so that each one is smaller then 4gb and all is splitted. There is not only one disk created even if all is smaller then 4gb.

So if this is some new requirement of the wubi 9x?

---

### Post by P4man on 2009-08-26
Like I said, i dont know much about wubi, didn't know it was that clever :).

Then again I googled and i read somewhere about a problem with wubi not recognizing a FAT32 filesystem correctly and proceeding as if it was an NTFS volume. That problem was fixed meanwhile, but dont have the link, not sure if it stil applies to you.

If that is not the problem, it could also be a corrupted download or cd Does wubi have a way to verify the integrity of the installer? If not, just boot the cd, and in the initial menu select "verify this cd/dvd for errors".

All that said, i would still recommend you install ubuntu on its own partition or drive if at all possible. Wubi is a hack.

---

### Post by ottosykora on 2009-08-26
inthe website I could so far find that , yes it creates smaller files on fat32 to split the disk.

But even the website seems to have been edited few days ago, there it still says it will work only with version 8x .

However the current wubi is placed on the ftp server under version 9 and is also bigger then the previous once. When I simply click wubi from ubuntu website I get the latest one which is placed under ubuntu 9x on the archive.

The file is checked prior installing as part of the process automatically, so it should not be broken. I have downloaded it 3 times after all and it was the same each time.


so all somehow confusing.

---

