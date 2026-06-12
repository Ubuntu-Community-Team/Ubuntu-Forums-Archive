---
title: "Move Documents to another partition"
date: 2009-07-23
forum: Installation &amp; Upgrades
---

### Post by notechyet on 2009-07-23
Hello
I have just installed Ubuntu and after all was up and running I created another partition for data. How do I shift; Documents,Pictures and Movies to that partition and also how do I make that this partition mounts at startup.

Thanks:D
NT

---

### Post by oldfred on 2009-07-23
You need to make a directory, mount the partition to the directory, give rights to the directory to you- chown and edit your fstab to make mount permanent, and finally  copy files. 
mkdir new_directory
sudo mount -t ext3 /dev/sdxy /media/new_directory    
             or /home/yourname/new_directory or where you want to see the new data
sudo chown yourusername:yourgroupname /mnt/mountpoint/
gksudo  gedit /etc/fstab
add line like after finding UUID of partition with:
blkid
UUID=UUIDofpart /new_directory ext3 nodev,nosuid,relatime 0 0
Then use 
cp -a old_directory new_directory
 where -a preserves attributes

see this for fstab info:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by merlinus on 2009-07-23
You may need to preface mkdir with sudo.

---

### Post by notechyet on 2009-07-23
Thanks guys.:D:D 
I will have a try.
Is it all through the terminal?
I'll let you know what my success is.

---

### Post by notechyet on 2009-07-23
Here below is my setup.
I want to place the documents, photos, e.g. on /dev/sda3
and get the partition to mount at boot up.


edward@edward-desktop:~$ sudo fdisk -l
[sudo] password for edward: 

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9aa39aa3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2008    16129228+  83  Linux
/dev/sda2            4693        4865     1389622+   5  Extended
/dev/sda3            2009        4692    21559230   83  Linux
/dev/sda5            4693        4865     1389591   82  Linux swap / Solaris

Partition table entries are not in disk order
edward@edward-desktop:~$

---

### Post by notechyet on 2009-07-23
> **oldfred said:**
> You need to make a directory, mount the partition to the directory, give rights to the directory to you- chown and edit your fstab to make mount permanent, and finally  copy files. 
mkdir new_directory
sudo mount -t ext3 /dev/sdxy /media/new_directory    
             or /home/yourname/new_directory or where you want to see the new data
sudo chown yourusername:yourgroupname /mnt/mountpoint/
gksudo  gedit /etc/fstab
add line like after finding UUID of partition with:
blkid
UUID=UUIDofpart /new_directory ext3 nodev,nosuid,relatime 0 0
Then use 
cp -a old_directory new_directory
 where -a preserves attributes

see this for fstab info:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

I'm trying as suggested but do not get further than the first line as it says(by repeating) file exists and when trying to mount it says: new_directory does not exist

---

### Post by notechyet on 2009-07-24
Obviously I haven't quite got it!

edward@edward-desktop:~$ sudo mkdir new_directory
[sudo] password for edward: 
mkdir: cannot create directory `new_directory': File exists
edward@edward-desktop:~$ mount -t ext3 /dev/sdxy /media/new_directory 
mount: only root can do that
edward@edward-desktop:~$ sudo mount -t ext3 /dev/sdxy /media/new_directory 
mount: mount point /media/new_directory does not exist
edward@edward-desktop:~$ sudo mount -t/home/edward/new_directory
edward@edward-desktop:~$ sudo chown edward:edward /mnt/mountpoint/
chown: cannot access `/mnt/mountpoint/': No such file or directory
edward@edward-desktop:~$ sudo chown edward:edward /mnt/mountpoint/gksudo gedit /etc/fstab
chown: cannot access `/mnt/mountpoint/gksudo': No such file or directory
chown: cannot access `gedit': No such file or directory
edward@edward-desktop:~$ sudo chown edward:edward/mnt/mountpoint/
chown: missing operand after `edward:edward/mnt/mountpoint/'

---

### Post by merlinus on 2009-07-24
Try this, in a terminal (I am using /data for the sda3 mountpoint, so change it to whatever you like):

```
sudo mkdir /data
sudo mount -t ext3 /dev/sda3 /data
```If this works, post back if you need help adding an entry to /etc/fstab so it mounts automatically.

---

### Post by notechyet on 2009-07-24
merlin
I tryed as above and had no success so I rebooted and tried again:
edward@edward-desktop:~$ sudo mkdir /data
[sudo] password for edward: 
mkdir: cannot create directory `/data': File exists
edward@edward-desktop:~$ sudo mount -t ext3 /dev/sda3 /data
mount: wrong fs type, bad option, bad superblock on /dev/sda3,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

edward@edward-desktop:~$ sudo chown edward:edward /mnt/mountpoint/
chown: cannot access `/mnt/mountpoint/': No such file or directory
edward@edward-desktop:~$

---

### Post by merlinus on 2009-07-24
Is sda3 formatted as ext3?

---

### Post by notechyet on 2009-07-24
> **merlinus said:**
> Is sda3 formatted as ext3?
merlin
it is ext2

---

### Post by notechyet on 2009-07-24
here my setup
[http://picasaweb.google.com/sezalped/Desktop#5361882441474014514](http://picasaweb.google.com/sezalped/Desktop#5361882441474014514)

---

### Post by merlinus on 2009-07-24
Then change ext3 to ext2 in the mount command.

---

### Post by notechyet on 2009-07-24
the fstab does not contain the needed partition, for the next step

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=af5f4992-3264-43c2-8b1f-727230e5dfa8 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=5b4eddaa-0e83-452e-9fa8-e4f5f4d32937 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


because that below is uuid output

edward@edward-desktop:~$ ls /dev/disk/by-uuid -alh
total 0
drwxr-xr-x 2 root root 100 2009-07-24 16:36 .
drwxr-xr-x 6 root root 120 2009-07-24 16:36 ..
lrwxrwxrwx 1 root root  10 2009-07-24 16:22 5b4eddaa-0e83-452e-9fa8-e4f5f4d32937 -> ../../sda5
lrwxrwxrwx 1 root root  10 2009-07-24 16:22 af5f4992-3264-43c2-8b1f-727230e5dfa8 -> ../../sda1
lrwxrwxrwx 1 root root  10 2009-07-24 16:36 d994a620-4a1b-4186-aefc-9e4c79f81421 -> ../../sda3
edward@edward-desktop:~$ 

so do I use the number of the sda3 for the fstab?
Thanks for your patience!

---

### Post by notechyet on 2009-07-24
Back again
I think I have succeeded with some untidy details to be seen in the image.
[http://picasaweb.google.com/sezalped/Desktop#5361903577960647234](http://picasaweb.google.com/sezalped/Desktop#5361903577960647234)
Can someone guide me to which folders I can delete?
Thanks

---

### Post by merlinus on 2009-07-24
If you mounted it on /data, then look in filesystem for that.

Then add this to the end of /etc/fstab:

/dev/sda3 /data ext2 relatime 0 1  

and restart.

If that works, you can then delete directory, new_directory and new from edward.

---

### Post by notechyet on 2009-07-24
merlin
I think it is not right what I did. Look here:
[http://picasaweb.google.com/sezalped/Desktop#5361946782111287490](http://picasaweb.google.com/sezalped/Desktop#5361946782111287490)

---

### Post by merlinus on 2009-07-24
Looks good to me.

---

### Post by notechyet on 2009-07-24
merlin
It does load at startup.
Though, the documents, videos, pictures are not within this mounted directory/partition.

---

### Post by merlinus on 2009-07-24
Are you sure these are in sda3?  If so, it is very strange that they are not showing up in /data.

Also, look in the directory, new_directory and new folders in /home, just in case they are showing up there.

---

### Post by notechyet on 2009-07-25
merlin
Thanks!
I'm just back from skiing,had beautiful weather and good snow.
I have deleted directory , new_directory and new folder without checking this first.
Anyway, I have been thinking if I should install again and add a data partition right from the beginning.
Though I would still have to shift documents, videos, fotos and music.
So, am I stuck now?

---

### Post by merlinus on 2009-07-25
If you have backups of your docs, etc., then it should be straightforward to copy them to the /data partition.  However, you might consider formatting it as ext3 first.

---

### Post by notechyet on 2009-07-25
merlin
Done the formating.
How do I link the the documents, videos, pictures with the data partition. If I just shift them accross those will not be visible in "places" in the file browser?

---

### Post by merlinus on 2009-07-25
Where are your docs, etc. located?

---

### Post by notechyet on 2009-07-25
> **merlinus said:**
> Where are your docs, etc. located?
Thanks
If you mean the folders;documents, videos, pictures, those are in the home folder.
see here:[http://picasaweb.google.com/sezalped/Desktop#5362481461849466498](http://picasaweb.google.com/sezalped/Desktop#5362481461849466498)
So what I like is to place home on data.

---

### Post by merlinus on 2009-07-25
No, **definitely** do not move /home to /data or ubuntu will not work!

You can create folders with the same names in /data, and move the files into those.

Another choice is to create a separate /home partition that will replace /data.  Info on how to do this here:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by notechyet on 2009-07-25
merlin
thanks for taking all that time to my questions, very generous of you!
I'll have a look at your suggestion.

---

### Post by merlinus on 2009-07-25
Glad to be of assistance.  Post back with questions, etc.

---

