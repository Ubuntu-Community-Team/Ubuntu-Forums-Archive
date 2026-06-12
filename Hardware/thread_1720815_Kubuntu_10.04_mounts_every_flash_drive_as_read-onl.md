---
title: "Kubuntu 10.04 mounts every flash drive as read-only"
date: 2011-04-03
forum: Hardware
---

### Post by mrblue8 on 2011-04-03
Hey, guys,

I'm a user of Kubuntu 10.04 and I can't write or delete files from any flash drive (pen drives, mp3 players...)

I have formatted them a couple of times but it is no longer working, besides I think that formatting it every time might harm the device...

Here's the entry from terminal

```
administrador@computador:/media/usb0$ cp "/home/administrador/Desktop/comparisons.odt" comparisons.odt
cp: cannot create regular file `comparisons.odt': Permission denied
```I have googled it everywhere but I can't find a solution for this

Thanks a bunch

---

### Post by SeijiSensei on 2011-04-03
Let's start with an easy question.  What are the ownerships and permissions on /media/usb0?  Oh, and what kind of file system is on the device? FAT32? NTFS? ext3/4?

```
cd /media
sudo ls -l 

```

to start with.  Does the "administrador" account have write permissions to /media/usb0?

---

### Post by mrblue8 on 2011-04-04
It says the user is 'root' but even if I try to copy files as sudo it doesn't work. 'Administrador' has sudo privileges.

```
administrador@computador:/media/usb0$ sudo cp "/home/administrador/Desktop/comparisons.odt" comparisons.odt
cp: cannot create regular file `comparisons.odt': Read-only file system
```Here's what I got from *ls -l*

```
administrador@computador:/media$ sudo ls -l
[sudo] password for administrador: 
total 40
drwxr-xr-x 2 root root 4096 2011-04-03 18:13 Datas
drwxr-xr-x 2 root root 4096 2010-12-25 10:14 force
lrwxrwxrwx 1 root root    4 2010-12-24 16:35 usb -> usb0
drwxr-xr-x 3 root root 4096 1969-12-31 21:00 usb0
drwxr-xr-x 2 root root 4096 2010-12-24 16:35 usb1
drwxr-xr-x 2 root root 4096 2010-12-24 16:35 usb2
drwxr-xr-x 2 root root 4096 2010-12-24 16:35 usb3
drwxr-xr-x 2 root root 4096 2010-12-24 16:35 usb4
drwxr-xr-x 2 root root 4096 2010-12-24 16:35 usb5
drwxr-xr-x 2 root root 4096 2010-12-24 16:35 usb6
drwxr-xr-x 2 root root 4096 2010-12-24 16:35 usb7
administrador@computador:/media$ cd /media/usb0
```And the flash-drive is FAT32, I think it's always been FAT32 but I formatted it using this filesystem

Thanks

---

### Post by mrblue8 on 2011-04-04
I also tried to run the commands as *root*

```
administrador@computador:~$ su root
Password: 
root@computador:/home/administrador# cd /media/usb0
root@computador:/media/usb0# sudo cp "/home/administrador/Desktop/comparisons.odt" comparisons.odt
cp: cannot create regular file `comparisons.odt': Read-only file system
```

but it still doesn't work

---

### Post by SeijiSensei on 2011-04-04
Now we've got a different error, a read-only filesystem rather than denial of permissions.  Usually Linux mounts a filesystem read-only when it has errors.  You can run a filesystem check with "fsck -t vfat /dev/sdX" replacing "X" with the appropriate drive identifier (sdb, sdc, etc.), or use "chkdsk" in Windows.

Have you tried all the USB ports on the machine?  Maybe it's a hardware problem.

Do you need to use this device on DOS/Windows as well as Linux?  If not, try formatting it as ext4 with "sudo mkfs -t ext4 -v /dev/sdX".

Did you disconnect this device from the machine without first using "Safely Remove"?  That can mark the device as having errors as well.

---

### Post by mrblue8 on 2011-04-04
during *fsck*, it asked me which FAT I wanted to use, so I ran the command twice to choose both FATs. Here's the result:

```
administrador@computador:~$ sudo fsck -t vfat /dev/sdb1
[sudo] password for administrador:
fsck from util-linux-ng 2.17.2
dosfsck 3.0.7, 24 Dec 2009, FAT32, LFN
FATs differ but appear to be intact. Use which FAT ?
1) Use first FAT
2) Use second FAT
? 1  
/Machete
  Contains a free cluster (3). Assuming EOF.
Reclaimed 1450229 unused clusters (5940137984 bytes).
Free cluster summary wrong (520189 vs. really 1970418)
1) Correct
2) Don't correct
? 1
Leaving file system unchanged.
/dev/sdb1: 2 files, 1/1970419 clusters
administrador@computador:~$ sudo fsck -t vfat /dev/sdb1
fsck from util-linux-ng 2.17.2
dosfsck 3.0.7, 24 Dec 2009, FAT32, LFN
FATs differ but appear to be intact. Use which FAT ?
1) Use first FAT
2) Use second FAT
? 2
/Machete/screencaps.jpg
  File size is 32768 bytes, cluster chain length is 4096 bytes.
  Truncating file to 4096 bytes.
Reclaimed 122618 unused clusters (502243328 bytes).
Free cluster summary wrong (520189 vs. really 1970415)
1) Correct
2) Don't correct
? 1
Leaving file system unchanged.
/dev/sdb1: 4 files, 4/1970419 clusters
```I have tried switching ports and trying different devices (my pen drive and the mp3 player). It randomly manages to copy and to not copy. But it never works on the file browser and it always fails when I don't type sudo on the command line. Well, it sounds random to me, but perhaps you can see the problem if you see the tries.

It worked here:
```
administrador@computador:/media/usb0$ sudo cp "/home/administrador/Desktop/comparisons.odt" comparisons.odt
```But it didn't here:
```

administrador@computador:/media/usb0$ sudo cp "/home/administrador/Desktop/correspondence.odt" correspondence.odt
cp: writing `correspondence.odt': Input/output error
administrador@computador:/media/usb0$ sudo cp "/home/administrador/Desktop/correspondence.odt" correspondence.odt
cp: writing `correspondence.odt': Input/output error
```And without sudo, it denies permission
```

administrador@computador:~$ cd /media/usb0/
administrador@computador:/media/usb0$ cp -r "/home/administrador/Desktop/comparisons.odt" comparisons.odt
cp: cannot create regular file `comparisons.odt': Permission denied
```Yes, I have disconnected it unsafely because Kubuntu would say "Permission denied" or something while I was using Dolphin, and I thought it wouldn't umount so I'd remove it anyway. However, I found out that I can umount it using the *umount* command with *sudo*.

And, yeah, unfortunately I will need to use it with Windows systems at work... But I know that the mp3 player works fine with the Windows computer.

Thanks!!

---

### Post by SeijiSensei on 2011-04-05
You should see the device in the left panel in dolphin.  If you right click on it, the "safely remove" option is available there.  It's also available via the connected devices applet in the task bar.  It's the circle with the little network diagram in it.  Clicking on that will bring up a list of attached devices; safely removing them is an option.

In both cases this won't work if something has the device open.  In dolphin, for instance, make sure to return to your home directory or some other location before using "safely remove."

---

### Post by mrblue8 on 2011-04-06
Yes, I used to do that on my previous Kubuntu version, it worked alright... But now, I can (sometimes) copy files using the terminal with *sudo* but I can never do it using Dolphin, even after correcting the errors, formatting the drives and removing it safely all the time. It says the user is *root* and doesn't let me write or erase files.

---

### Post by mrblue8 on 2011-05-04
I think I found a solution to my problem: *pmount*. I found it in an Ubuntu help page about mounting and umounting. This page should have been my first option, but I typed my problem on Google, and because I didn't find anything I came here for help... the Ubuntu help page had the answer all along! : ) But I still want to thank SeijiSensei for all the help and attention : )

The Ubuntu help page on mounting USB drives:
[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

Thanks

---

