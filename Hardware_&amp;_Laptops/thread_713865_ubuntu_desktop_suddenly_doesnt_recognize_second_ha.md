---
title: "ubuntu desktop suddenly doesnt recognize second hard drive"
date: 2008-03-03
forum: Hardware &amp; Laptops
---

### Post by SECProto on 2008-03-03
Hey all, I have two hard drives in my desktop - the SATA main one, with ubuntu and a few ntfs partitions on it, and i have an IDE hard drive with only one partition on it (label hdb1)
I added the IDE drive a month after installing ubuntu, and I had it all set up to automount, and all was well. Then, I was working in KDE 4, and some glitches were happening, and i tried to use KDE's update thing and it messed up, so I decided that was enough, and restarted to go into GNOME. Suddenly, Ubuntu does not recognize my second drive. It does not show up as mounted, or as unmounted, or anything.

On restarting into windows (which I hate doing), windows recognizes the drive fine. so it is just a problem with how ubuntu is configured.

Anyone have any ideas?

---

### Post by lswest on 2008-03-03
can you post your /etc/fstab file (or the relevant section) and the output of ```
fdisk -l
```  might help to figure some things out.  Also, what does it tell you if you try to mount it manually?  ```
sudo mkdir /media/[mountpoint]
sudo mount /dev/hdb1/ /media/[mountpoint]
```  any errors?

---

### Post by SECProto on 2008-03-03
Thanks for the response - i feel kind of silly now. i had forgotten to try manually mounting it - when I do that, it works fine. I must have deleted the directory I had fstab mounting it to.

The relevent line in fstab says:

# /dev/hdb1
/dev/hdb1       /media/big2     ntfs    defaults,umask=007,gid=46 0       1

I believe i just copied the lines from one of the other partitions and changed the directories - they are all ntfs so i assumed no difference.

It mounts it to that directory fine. My last question now is : how do I get the drive to show up in the places menu, and on the desktop? it used to before all this.

Very much appreciated!

Liam

---

### Post by lswest on 2008-03-03
to add it to the desktop you can run ```
gconf-editor
``` in the terminal, and then navigate to apps-->nautilus-->Desktop and check a box, not 100% sure what it's called (doing this from memory from a windoze box :S) but it refers to hard disks or so, you should spot it.  Also, do you mean to say you can mount it automatically now? or is it only being mounted manually?

---

### Post by Brixtontechnical on 2008-03-03
I have a similar problem which just happened - I have a Dell laptop with two hard drives in it. I installed Ubuntu on the secondary hd and had many problems with the video (another story). I ended up re-installing Ubuntu on the secondary drive, and in the effort to do so I had to remove the existing partitions to make space. I wanted a dual boot system (XP and Ubuntu)

I re-installed Ubuntu on the secondary drive by removing the original partitions and making a new partition, and now it runs fine. However neither XP nor Ubuntu now recognizes the second hd despite the fact that Ubuntu is loaded on it. (XP is loaded on the primary drive). I obviously messed up with the partitions when I made the re-installation - but how can I now find this drive and make the data that is on it accessible? Any suggestions?

---

### Post by Brixtontechnical on 2008-03-03
Never mind my question - I found out what I did. When I changed the partitions I accidently re-partitioned the whole drive and the remaining part of the drive was unallocated. I have to partition the remaining section of the drive to make it useable - if this makes sense. Thanks anyway.

---

### Post by SECProto on 2008-03-05
thanks for the help, lswest :) It works like a charm now - i didnt have a chance to restart until now. i must have deleted the /media/big folder that the drive was originally supposed to be mounting to.

---

