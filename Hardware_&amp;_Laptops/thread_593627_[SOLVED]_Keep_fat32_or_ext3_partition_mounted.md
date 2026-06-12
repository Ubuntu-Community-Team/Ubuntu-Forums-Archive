---
title: "[SOLVED] Keep fat32 or ext3 partition mounted"
date: 2007-10-27
forum: Hardware &amp; Laptops
---

### Post by Matticus on 2007-10-27
Could someone please help me to mount and keep mounted a fat32 partition.

I have split my laptop hard drive up, to have my swap partition, ubuntu partition, storage partition, and a newly created mepis partition.

The storage was ext3, but when I mounted it just by right clicking and mounting I couldnt do anything with it because the permissions where set to root, and I used "sudo nautilus" but for some reason it would let me navigate to the drive to change the permissions.

So I formatted to fat32, now I have full permissions, but it wont stay mounted after boot.

I tried another threads solution, to edit /etc/fstab, but I wasnt sure of the full procedure, the thread seemed to assume too much knowledge on part of the user, unfortunatly I dont have that knowledge.

So could anyone let me know what to do, the partition is /dev/hda4 and when its mounted its mounted as mount/disk.

also how to i change the name, it wont let me. and only linux will be accessing this drive, so shall i have it fat32 or ext3 or what else?

---

### Post by taurus on 2007-10-27
I recommend you reformat it back to ext3.  Then, edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it for your /dev/hda4.

```
/dev/hda4   /media/hda4   ext3   defaults   0   1
```
Save it.  Then, create a mount point and mount it.

```
sudo mkdir /media/hda4
sudo mount -a
df -h
```
Now, if you want to be able to write to it without using sudo, you need to change the ownership of /media/hda4 from root to your login name.  _Assuming_ your login name is matticus (replace it with the right one, okay), run

```
sudo chown -R matticus:matticus /media/hda4
ls -la /media
```

---

### Post by Matticus on 2007-10-27
Thank you very much.

It all worked perfectly, although...


Code:

sudo mkdir /media/hda4
sudo mount -a
df -h

I had some issues with the above, as it said it already existed, I figured that it had just done automatically what I was about to do manually. So I didnt worry too much.

Once I had set the permissions I tried the drive and it was still root, but after a restart the drive showed up nicely and I was the owner and had all the permissions.

To change the name it shows up as from hda1 to something, do I just change where it mounts?

Thanks again

EDIT : Also I precreated the MEPIS partition ready for installation, but the installation crashed earlier, and caused my harddrive to be slightly bricked.
Basically it killed the first partition which used to have windows on it, therefore killing the mbr, it would have been ok, but it crhased midway of formatting, so I was left with free space. I downloaded partedmagic live cd, and just formatted hda4 and hda1 into one ext3, and then did this and everything is sorted, apart from ubuntu not seeing my swap, but that is for another thread.

---

### Post by taurus on 2007-10-27
If you don't want to mount it to /media/hda4, then you need to edit /etc/fstab and change it to the new mount point.  Don't forget to create it if it's not already there.  Also, you need to change the ownership of the new mount point to your login name or only root can write to it.

---

### Post by taurus on 2007-10-27
> **Matticus said:**
> T

EDIT : Also I precreated the MEPIS partition ready for installation, but the installation crashed earlier, and caused my harddrive to be slightly bricked.
Basically it killed the first partition which used to have windows on it, therefore killing the mbr, it would have been ok, but it crhased midway of formatting, so I was left with free space. I downloaded partedmagic live cd, and just formatted hda4 and hda1 into one ext3, and then did this and everything is sorted, apart from ubuntu not seeing my swap, but that is for another thread.

Post the outputs of these commands from terminal and we will fix the swap partition as well?

```
free
sudo fdisk -l
cat /etc/fstab
```

---

### Post by Matticus on 2007-10-27
oops sorry taurus, I posted the other thread before either you replied to this or I noticed.
But the problem is all fixed now, so thanks a lot for your help.

---

### Post by bmwerks on 2007-10-28
thanks this was a big help been trying to figure this for a while, but my permissions still haven't changed

---

### Post by Matticus on 2007-10-28
> **bmwerks said:**
> thanks this was a big help been trying to figure this for a while, but my permissions still haven't changed

Did you make sure you changed my name "matticus:matticus" to your user name, I think, though I dont know that the first one is the group name and the second is the user name.

Oh and make sure you restart, the permissions wont come into play until your restart.

---

### Post by bmwerks on 2007-10-29
yeah i have restarted and changed the name i also had to change hda1 to sda1 took me a while to figure that out though

---

