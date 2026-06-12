---
title: "Mounting a hard drive in 8.04"
date: 2008-09-28
forum: General Help
---

### Post by Roflcopter939 on 2008-09-28
I recently installed a 40GB storage drive in my Ububox.  The issue I'm having is how to mount it so that I have access to it.  I know there's probably a really easy solution for this but I haven't been able to find one in my browsing.  Basically the drive shows on my desktop, but the permissions are set for root only.  I added the drive in fstab, maybe not correctly, in /media/storage, and when I type in the "mount" command, the storage drive is listed as,
/dev/sdb1 on /media/disk type ext3 (rw,nousid,nodev,uhelper=hal)
Just trying to get it to mount at boot and be able to read/write to it!
Thanks!

---

### Post by Victormd on 2008-09-28
Take a look at my signature to automount on Hardy... :)

---

### Post by Roflcopter939 on 2008-09-28
Thanks VictorMD there's a ton of good info there.
I added the drive using the UUID number in fstab, now it looks like this,
/dev/sdb1
UUID=3bb50eb7-c034-4401-9d6b-9f0261fd856e /media/disk ext3 defaults,umask=007,gid=46 0 0 
but when I did that it totally went away, it's not in my Places folder, and I don;t know how to get it back other than deleting that line.  Now what :confused:

---

### Post by louieb on 2008-09-28
Its confused - you need to comment out the 1st line.
```
[COLOR=Red]#[/COLOR]/dev/sdb1
UUID=3bb50eb7-c034-4401-9d6b-9f0261fd856e /media/disk ext3 defaults,umask=007,gid=46 0 0 
```

Then after commenting out the line make it mount by using.
```
sudo mount -a
```

---

### Post by Roflcopter939 on 2008-09-28
Well I thank you for your help, this is a day for noobtastic mistakes.  One more error message and I feel good about this being the last one.  Got rid of that line, then typed
sudo mount -a
and got
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
do I need tabs in between all those things? I only have spaces.  I'm thinking I'm just glad I can open Firefox :oops:

---

### Post by Roflcopter939 on 2008-09-28
Ok so removing the first line of code by placing the # in front of it means the disk is back in my Places list, but when I go to mount it by clicking on it, I get a message saying
You are not privileged to mount the volume.
Did I do something wrong in Fstab to prevent a user from mounting it?

---

### Post by louieb on 2008-09-28
Spaces between parameters in fstab are fine.

Try changing permissions for the mount point. to give everybody read, write permission.
```
sudo chmod 777 /media/disk
```

Knowing the chmod and chown commands is useful when dealing with permissions.

---

### Post by Roflcopter939 on 2008-09-28
I was able to mount the drive using the "mount" command, then use "chmod" to give myself permission to move my music over to the drive.  Then I installed updates and restarted my computer.  The drive was unmounted and I once again could not mount it due to permission issues.  Is there a way to auto mount it on start-up in a way that gives me permission to write to it?  Why is it so difficult to install a second hard drive, its one of the most performed hardware upgrades in my opinion, there should be a gui.

---

### Post by Victormd on 2008-09-28
You can replace the umask=007 to umask=0000 (this grants access to everyone). Also, you can replace gid=46 to gid=root (gid = group ID)
> UUID=3bb50eb7-c034-4401-9d6b-9f0261fd856e /media/disk ext3 defaults,**umask=0000,gid=root** 0 0
Another alternative is to remove umask and gid so your fstab line will look like this:
> UUID=3bb50eb7-c034-4401-9d6b-9f0261fd856e /media/disk ext3 defaults 0 0
I like the umask and gid options because they allow me to manage my HDs' access. This is interesting to use when you have more than 1 person using the computer under different user names... just a bit more security to your files.

---

### Post by yarn on 2008-09-28
hey i had the same problem...i could mount my Hard disk and not be able to get permission for it...check out what helped me out...might work for u                   [http://ubuntuforums.org/showthread.php?t=880457](http://ubuntuforums.org/showthread.php?t=880457)

---

### Post by acdcfan on 2008-09-29
> **yarn said:**
> hey i had the same problem...i could mount my Hard disk and not be able to get permission for it...check out what helped me out...might work for u                   [http://ubuntuforums.org/showthread.php?t=880457](http://ubuntuforums.org/showthread.php?t=880457)

How do you permanently mount drives on your desktop? Can you please post how to?

---

### Post by Victormd on 2008-09-29
> **acdcfan said:**
> How do you permanently mount drives on your desktop? Can you please post how to?

Take a look at my signature on How to automount in Hardy... :)

---

