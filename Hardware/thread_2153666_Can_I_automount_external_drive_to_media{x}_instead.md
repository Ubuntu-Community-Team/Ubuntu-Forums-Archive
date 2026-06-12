---
title: "Can I automount external drive to /media/{x} instead of /media/[user]/{drivelabel}"
date: 2013-06-11
forum: Hardware
---

### Post by jfb3 on 2013-06-11
When I plug in an external drive it automounts to/media/jfb3/{DriveLabel}.  

I created a directory in /media/TowerOfFiles 

I created an entry in fstab:
UUID={uuid} /media/TowerOfFiles


No joy.

I don't want to turn off automounting of all external media, just for this drive.

What do I need to do?

OS version: 13.04

---

### Post by ahallubuntu on 2013-06-11
~

---

### Post by jfb3 on 2013-06-11
I did make the directory first (that's why I listed that step first).

So, I changed the mount point to be under /mnt (because why not).

Either fstab entry:
```
UUID=AA70755970742D67     /mnt/TowerOfFiles     ntfs
```

```
UUID=AA70755970742D67     /mnt/TowerOfFiles     ntfs-3g
```

Still no joy.  
Produced the same result. 
It still gets mounted at /media/jfb3/TowerOfFiles.

---

### Post by Morbius1 on 2013-06-12
Install bindfs:
```
sudo apt-get install bindfs
```
Create a new directory:
```
sudo mkdir /Disks
```
The line in fstab would look like this:
```
bindfs#/media/jfb3 /Disks fuse mirror=jfb3 0 0
```
Then run:
```
sudo mount /Disks
```
Or reboot

When you plug in a USB device it will mount to the original mount point and to /Disks/LABEL

[COLOR=#0000cd]*BTW: You are never ending the sentence you are creating in fstab. You have nouns but no verbs. This:*[/COLOR]
> UUID=AA70755970742D67     /mnt/TowerOfFiles     ntfs
Should at least be this:
> UUID=AA70755970742D67     /mnt/TowerOfFiles     ntfs defaults 0 0

---

### Post by jfb3 on 2013-06-12
Your "solution" is all well and good.
But it doesn't solve my problem.


But the question remains:  
Why can't I get a disk to mount where I want it and not under some random levels of directories and some random username?
Why does the drive not get mounted where I want? 
It also won't mount unless I'm logged in as this user.  That's unacceptable.
Should I go ahead and report this bug?

---

### Post by ahallubuntu on 2013-06-12
~

---

### Post by Morbius1 on 2013-06-12
I have had some heated arguments over my approach to a problem before but I never had my "solution" put in quotes before.  :KS

> Why can't I get a disk to mount where I want it and not under some random levels of directories and some random username?
You can and the default method is not random. For an external device it will mount to /media/$USER/LABEL where $USER is the person who inserted the device.
> It also won't mount unless I'm logged in as this user. That's unacceptable.
If you truly mean "mount" your assignment for the day is to investigate what the group "plugdev" does.
> Should I go ahead and report this bug? 
Funny thing about a development group - a bug is defined as something that happens outside of the design parameters. A user might consider something a bug if it doesn't do what he wants it to do. Under that definition I consider Unity a bug. But to the developers it's doing exactly what they were told to build so it ain't no bug.

---

### Post by jfb3 on 2013-06-12
I can (and did) disable automounting (I knew how to do that).
But that means that nothing is ever mounted automatically (not what I wanted).

Yeah I know that I didn't show the entire fstab entry for mounting that drive (it's too much typing on another computer).

Working, but not happily resolved.

---

