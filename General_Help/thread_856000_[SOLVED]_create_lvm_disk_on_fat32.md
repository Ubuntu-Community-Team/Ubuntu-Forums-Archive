---
title: "[SOLVED] create lvm disk on fat32"
date: 2008-07-11
forum: General Help
---

### Post by tramir on 2008-07-11
First of all, sorry for cross-posting. 
Here's the situation: I have a NAS that accepts only FAT32-formatted hard disks. I am trying to create an ext3 partition on it to sync/backup my home partition. The way I found (still open to suggestions) is to create a bunch of files, assign them to loopback devices with losetup, and create an  LVM (please ignore the inefficiencies of the code - noob here):

```
MNTPT="/media/Mircea_Backup"
PART_LIST=""

for i in $(seq 1 5); do 
  j=$(printf %02d $i)
  dd if=/dev/zero of=$MNTPT/ext3_part${j} bs=4096 count=1500
done

for i in $( ls $MNTPT/ext3_part* ); do
  j=${i:30:3}
  k=$(($((10#$j)) - 1))
  echo "sudo losetup /dev/loop${k} ${i}"
  sudo losetup /dev/loop${k} ${i}
  PART_LIST="${PART_LIST} /dev/loop${k}"
done
sudo pvcreate ${PART_LIST}
sudo vgcreate backupsys ${PART_LIST}
sudo lvcreate --name bckup --extents 100%FREE backupsys
sudo mkfs.ext3 /dev/backupsys/bckup
```
It all works fine, or at least it seems to. The problem is when I disconnect from the NAS or reboot. The vg is lost, and if I try to retrace my steps (losetup, pvcreate, vgcreate etc), it doesn't recognize the already-existing partition etc. I know I'm doing something wrong, but I don't really know what (it's my first attempt to work with LVM). Can somebody help me here? What should I do to make sure I can still access/recreate the LVM even after disconnecting from the NAS or rebooting? Or, God forbid, upgrade Ubuntu :) TIA

---

### Post by sdennie on 2008-07-11
Why not avoid LVM (which I don't think is appropriate for your situation) and instead use something like rsync or sbackup to write directly to the fat32 disk (not sure if rsync will work but, google for "rsynce to fat32").

Edit:
I see partimage being recommended a lot on the forums as well.  You may want to take a look at that too.

---

### Post by tramir on 2008-07-11
Yeah, I know of rsync/unison, which do pretty much the same thing. The problem, as you know, is that you can't save permissions on fat32 and I'd really want to do that. Partimage is nice, but if I need only one or two files from the NAS, I don't think I can do that with it.

In the end, the idea is that I would like to be able to sync the NAS with my home partition (which should take significantly less time than a full backup) and be able to have file-level access to my "backup". If you an idea other than LVM, please let me know (I also tried using a VMWare disk, but that didn't really work). Thanks...

---

### Post by tramir on 2008-07-11
Never mind, I figured it out in the end. I can create an LVM disk using loopback files, but now I run into CIFS problems. See [this thread]("http://ubuntuforums.org/showthread.php?t=856877").

---

