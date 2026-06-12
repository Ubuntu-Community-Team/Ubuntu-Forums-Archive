---
title: "dd help please!"
date: 2008-10-09
forum: General Help
---

### Post by daverave999 on 2008-10-09
I've looked at the man page and searched the web but to no avail. A newbie error I imagine...

I'm trying to transfer the contents of a hard drive mounted at /media/disk to a remote NFS folder mounted at /backupfolder using the command
```
sudo dd if=/media/disk of=/backupfolder
```

Simple problem is, they are directories so it doesn't work. How can I make this work?

Thanks in advance!

[EDIT: I've tried all variations of wildcards I can think of too]

---

### Post by jerome1232 on 2008-10-09
edit:After re-reading your post dd isn't what you want, go with mihaiv's suggestion, another good tool for copying files is rsync. It's better then cp in this intance becuase the next time you run it, it will figure out what's changed and update you backup accordingly (using much less bandwidth on subsequent backups)

```
rsync -avz source destination
```

[COLOR="Red"]dd doesn't seem to be what you want

You are tying to image a mounted partition which is a no no.
You need to figure out what device your trying to image then unmount it and use the device as the input argument, for the output you need to output to an actual file.

replace /dev/sdx# with the actual device (/dev/sda1, sda2, sdb3 whatever it is)

```
[COLOR="Red"]mount   #find the one that's mounted at the location you were trying to copy
sudo umount /dev/sdx#
sudo dd if=/dev/sdX# of=/backupfolder/sdx#.img[/COLOR]
```[/COLOR]

---

### Post by mihaiv on 2008-10-09
Why are you using dd for this? Looks like a job for cp.
**cp -R source_folder destination_folde**r

---

### Post by daverave999 on 2008-10-09
Much appreciated both.
I was using dd because I didn't know if cp would transfer hidden files and I wanted to get the lot, just to make sure I didn't miss anything.

Will cp do this? Is that what the --copy-contents switch is for?

[EDIT: I'm only needing to do this the once but rsync looks useful for other purposes]

---

### Post by jerome1232 on 2008-10-09
cp copies hidden files with no extra flags
```
jeremy@direbane:~$ ls test
backup
jeremy@direbane:~$ ls -a test
.  ..  backup  .joe
jeremy@direbane:~$ cp -r test Backup/
jeremy@direbane:~$ ls Backup/test
backup
jeremy@direbane:~$ ls -a Backup/test
.  ..  backup  .joe
jeremy@direbane:~$ 
```

---

### Post by caljohnsmith on 2008-10-09
In order to handle symbolic links and special cases like that correctly when copying an entire file system, I usually use:
```
cp -ax <input directory> <output directory>
```
That handles symbolic links and also preserves modes, ownership, and timestamps, so you get a truer "copy" of the file system. :)

---

