---
title: "Can't Add Folder To USB External"
date: 2008-11-14
forum: General Help
---

### Post by Rodney9 on 2008-11-14
Hello ,

I just plugged a 320Gb USB external hard drive in , it auto mounts but will not let me add a folder, how do I ?

I installed sudo aptitude install ntfs-3g ntfs-config
and ran gksu ntfs-config, enabled write support for external drive, then rebooted but still can not add a folder.


Rodney.

---

### Post by Rodney9 on 2008-11-14
I just plugged a 320Gb USB external hard drive in my PC running Ubuntu 8.10 64bit, it auto mounts but will not let me add or read a folder.

It is formatted hfsplus, I have turned off journaling and have hfsplus and hfsutils installed.


Well it seems I can read/write at root, so I am coping all the files/photos off it that I need.

What and how would be the best way to format this external drive ?

Rodney.

---

### Post by WWSmith36 on 2008-11-15
This definately sounds like a permission issue.  You should change the permissions on the drive to allow you have read/write without using root.

```
sudo chown $USER:$USER /media/device-name
sudo chmod -R 750 /media/device-name
```

Hope this helps

---

### Post by Rodney9 on 2008-11-15
> **WWSmith36 said:**
> This definately sounds like a permission issue.  You should change the permissions on the drive to allow you have read/write without using root.

```
sudo chown $USER:$USER /media/device-name
sudo chmod -R 750 /media/device-name
```

Hope this helps

Thank You.

But I have copied the files to my home folder.

Gparted seems to be the answer for formating.
However before I do I want to be able to see in the folders I copied, even in home folder I can't read some, how do I fix this.

---

### Post by Rodney9 on 2008-11-15
I tried sudo chown $USER:$USER /dev/sdd1

sudo chmod -R 750 /dev/sdd1 

as /media/device-Elements Back-UP wouldn't find it.

Anyway I still can not read the folders on the external or the ones I copied into Home.

---

### Post by Rodney9 on 2008-11-15
I used -
sudo chown -R rodney:rodney MacPhotos
for the folders I copied to my Home folder.

Now I can read them in my Home folder.

For the usb external drive would formating fat32 using gparted help prevent these problems in the future.

Also will I be able to rename the drive ?

---

### Post by blackened on 2008-11-15
Formatting isn't really necessary, but you it would solve the issue if you really want to do it that way. The reason chmod didn't work on the external drive is because you were trying to modify the permissions on the device file itself, which you can't do. You need to modify the permissions for the mountpoint, which apparently you tried, but used the wrong mountpoint name (you misunderstood the directions given by WWSmith36).

Replace the bold parts with the correct info pertaining to your system (for **$USER** use your username, for **device-name** use the drive's label in /media) so:
```

sudo chown **$USER**:**$USER** '/media/**device-name**'
sudo chmod -R 750 /media/

```

---

### Post by Rodney9 on 2008-11-15
For the usb external drive would formating fat32 using gparted help prevent these problems in the future.

Also will I be able to rename the drive to something easy like wd320 ?

---

### Post by blackened on 2008-11-15
FAT32 does not use permissions like ext3 and ntfs do, so yes, it should make it easier for you to mount the drive properly. Really the filesystem doesn't matter much when it comes to labelling. You can leave it as NTFS and label it something easy using the program 'ntfslabel'.

---

