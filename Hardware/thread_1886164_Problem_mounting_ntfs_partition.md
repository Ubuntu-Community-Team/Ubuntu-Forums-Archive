---
title: "Problem mounting ntfs partition"
date: 2011-11-24
forum: Hardware
---

### Post by nokiau on 2011-11-24
Hello guys! I have a litle problem when I'm trying to mount a ntfs partition in Ubuntu 11.04. When I'm trying to mount the partition, I recive the following error:
```
Unable to mount DATA
One or more block devices are holding /dev/sda6
```
Here is a screenshot from gparted:
[http://imageshack.us/f/507/gparted.png/](http://imageshack.us/f/507/gparted.png/)
I have installed on my pc windows 7 and backtrack RC5(sda4 is for backtrack).
What should I do to mount DATA partition? OS partition works very well in Ubuntu and in Backtrack both OS and DATA are working perfectly.
Thank you in advance!

---

### Post by BC59 on 2011-11-24
There is a similar problem here

[http://ubuntuforums.org/showthread.php?t=1606339](http://ubuntuforums.org/showthread.php?t=1606339)

and here in Fedora forums, but it's relevant

[http://forums.fedoraforum.org/showthread.php?t=249580](http://forums.fedoraforum.org/showthread.php?t=249580)

---

### Post by nokiau on 2011-11-30
Thanks for the answer, but it didn't help me :( Other solutions?

---

### Post by BC59 on 2011-11-30
I found this let's see if it's working for you:

1. You need to make permanent home for the ntfs partition into which it can be stored. To make permanent home for the ntfs partition you may need to type the following command in the terminal window:

```
sudo mkdir /media/WinBackUp
```

2. The above command will take the backup and it will be stored in the location given by you.

3. After taking a backup you may need to add a line to the fstab by typing the command given below:

```
/dev/sda5 /media/WinBackUp ntfs defaults,nls=utf8,umask=007,uid=1000,gid=46 0 0
```

4. Now you can type the below command in the fstab file which will mount the ntfs partition.

```
sudo mount –a
```

5. Now the ntfs partition will be mounted automatically without any problem.

---

### Post by nokiau on 2011-12-01
Still not working :( When I run sudo mount -a I recive the follwoing error:

fuse: mount failed: Device or resource busy

---

### Post by Mark Phelps on 2011-12-01
How do you know that it's not already mounted?  That would give you an error if you tried to mount it again.  Have you checked your /etc/fstab to ensure that it isn't being mounted by default?

---

### Post by nokiau on 2011-12-01
Yes, I checked. It is not mounted.

---

### Post by nokiau on 2011-12-03
Any other suggestions?

---

### Post by fdrake on 2011-12-03
the error is in  task #2
> 
/dev/[COLOR="Red"]sda5[/COLOR] /media/WinBackUp ntfs defaults,nls=utf8,umask=007,uid=1000,gid=46 0 0

it should be:
```
/dev/sda6 /media/WinBackUp ntfs defaults,nls=utf8,umask=007,uid=1000,gid=46 0 0
```
also if you want write permisssions I would change the type to "fuseblk" (after you have installe "ntfs-3g" and  "libntfs-3g75")

---

### Post by nokiau on 2011-12-03
I had seen that mistake before I made the changes. It doesn't work.

---

### Post by fdrake on 2011-12-03
```

sudo lsof /dev | grep sda6

```
check which process is keeping the partition busy.

---

### Post by nokiau on 2011-12-03
I got this :
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/andrei/.gvfs
      Output information may be incomplete.

The folder .gvfs is empty!

---

### Post by fdrake on 2011-12-03
yeah.. that's actually normal, but i was also expecting something else like a process name keeping the device busy:
> 
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/jorid/.gvfs
      Output information may be incomplete.
mount.ntf 15746  root    3u   BLK   8,17 0x7470980000 1073208 /dev/sdb1

i guess it's not a process thta't keeping the device busy!

---

### Post by nokiau on 2011-12-04
Yes, I guess it's not a process. Any other ideas?

---

### Post by Mark Phelps on 2011-12-05
OK, I know it's a shot in the dark ... but I'm guessing this is a dual-boot PC, right? 

Is there any chance that the Data partition was last used while in Win7, and you have Win7 either Hibernating or Sleeping -- while trying to access the partition from Linux?

---

### Post by fdrake on 2011-12-05
> **Mark Phelps said:**
> OK, I know it's a shot in the dark ... but I'm guessing this is a dual-boot PC, right? 

Is there any chance that the Data partition was last used while in Win7, and you have Win7 either Hibernating or Sleeping -- while trying to access the partition from Linux?

+1 , i think that may be the case too. It happened to me too different time when I hard booted the pc without shuting down windows. It's worth a shoot...

---

### Post by nokiau on 2011-12-06
It has 3 operating systems(ubuntu 11.04, windows 7 and backtrack rc5). Windows is not in hibernate or in sleep.

L.E. I can mount any other partition(including OS partition from windows) without any problem.

---

### Post by nokiau on 2011-12-13
Any other ideas???

---

