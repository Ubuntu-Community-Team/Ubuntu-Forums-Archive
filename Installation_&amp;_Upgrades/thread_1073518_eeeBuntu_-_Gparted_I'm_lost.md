---
title: "eeeBuntu - Gparted I'm lost"
date: 2009-02-18
forum: Installation &amp; Upgrades
---

### Post by MuRRe on 2009-02-18
Hi!
I would love to install eeeBuntu to my EEE pc.
Now, I'm having hugh problems.

I have the live-cd on an USB-stick. I load it in and evertyhing is fine. I can surf, install software and so on.

The problem comes when I try and install.
I just don't understand the Gparted software. It's really different from Vista/XP reformating tools (which I have used alot).

Now, I have 1 HDD which 80 GB. The HDD is split in half (acutally is 53% (where I have XP) and the rest is empty). 

On the empty space I want Ubuntu.
I can choose the Guided. What this seem to do is leave the XP partition alone and create to partitions inside the empty one (im not 100% sure though).

I can also choose Manual. But this doesn't really do what I want either since it seems to take the two partitions and put them together.

What I think I want for the second partition is this:
out of around 35GB i was thinking:
1. OS, around 5 GB???
2. /home for storing all the files (is this correct?)atleast 25GB would be nice?
3. /temp , do i need this and how big?
4. /swap (i have 1GB put planning to upgrade to two), how big? Double the RAM?

Now, if I do choose to skip XP it's not to hard to take those 40GB and give the to them /home partition right?

Im really sorry for this noobishness. I usually find out all answers myself (when it comes to Windows) but this time I'm a little confused.

Thanks in advance
MuRRe

---

### Post by InspiredIndividual on 2009-02-18
When I started dual booting Windows and Ubuntu, I found this link quite useful:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

You might not need it, as you've done a lot of partitioning already. Here is the link to a comprehensive HOWTO, very useful: [http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

About Gparted: you can just use the Manual option. It only seems to put the two partitions together, it doesn't start erasing your Windows partition immediately or anything. Further on, this link might get you started with Gparted: [http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted).

Just a last thing regarding your question about skipping XP: 
> 
If you want to resize a partition or add more space to an existing partition, keep in mind that you can add only to the end of a partition, not to the beginning of it.

If your Windows partition is the beginning of the disk and you want to add it to the next partition, you can erase the Windows partition, move the next partition to the beginning and add the free space to it. That's how I did it myself. Keep in mind some advise you to backup the data on a partition before moving it. I did so myself, although it turned out to be unnessecary in my case.

---

### Post by dstew on 2009-02-18
For starters, let's do something simple to see what your hard disk partition structure is at present. From the Ubuntu Live USB stick boot, open a terminal (I think in Applications --> Accessories) and enter on the command line```
sudo fdisk -l
```That will output a list of your partitions as seen by Ubuntu. Post the output to the forum.

---

### Post by MuRRe on 2009-02-18
> **dstew said:**
> For starters, let's do something simple to see what your hard disk partition structure is at present. From the Ubuntu Live USB stick boot, open a terminal (I think in Applications --> Accessories) and enter on the command line```
sudo fdisk -l
```That will output a list of your partitions as seen by Ubuntu. Post the output to the forum.


Disk /dev/sda: 80.0 GB, 80026361856 bytes
128 heads, 63 sectors/track, 19382 cylinders
Units = cylinders of 8064 * 512 = 4128768 bytes
Disk identifier: 0x13662e6d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10403    41944864+   7  HPFS/NTFS
/dev/sda2           10404       19374    36171072    7  HPFS/NTFS
/dev/sda3           19375       19382       32256   ef  EFI (FAT-12/16/32)

Disk /dev/sdb: 1031 MB, 1031798784 bytes
16 heads, 32 sectors/track, 3936 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3936     1007600    b  W95 FAT32


I was thinking maybe I could use Gparted before i run the install?
The interface while installation is not to nice.

So, basically now what I need to know is.
What file system should I use and what sizes of them? /var /temp /home and so on...

---

### Post by dstew on 2009-02-18
It looks like you have about 40 Gb empty space on the drive. And yes, I generally partition before installing. It makes the installation step much less anxiety-provoking. I use GParted from the [Gparted Live CD]("http://gparted.sourceforge.net/livecd.php").  I usually only make a root partition (format ext3, mount point "/") and a swap partition (no mount point -- designate it as "Use as swap"). If you think you want to install other linux distributions, and keep your files and settings the same, you might make a home partition (format ext3, mount point /home). I have not seen much use of a /temp partition.

I would make the root partition at least 10 Gb, and the swap partition 2 x the size of your RAM, or 1 GB, whichever is smaller.

---

### Post by MuRRe on 2009-02-18
Actually its 34.5GB.
So the structure will look like this BEFORE install:
Windows Partition
Root 10GB I cant set it in Gparted to /, do you do this later?
Swap 1GB (I have 1GB of RAm today, if i make it to 2 will 1GB swap stil be sufficient?) set filesystem to linux-swap

So I will just put all my data on the root?
Whats the difference between a /user and /home?
Also, will I make the /home (if thats where you usually put your files) AFTER I have installed Ubuntu then?


EDIT: Now when I go to Install, when it comes to the Gparted it doesnt show anything. I cant choose any partitions and all buttons are greyed out.
How do I mount with gparted?

I think I made it.
I have a / and a /swap.

Im just restarting after installing!!!

It works, YAY.

Is there anything i should do before starting to install my fav software?
Also, should I mount a /home partition for storing files or can I just make an ordinary disc somehow??

Thanks for all help!

---

### Post by dstew on 2009-02-18
> Also, should I mount a /home partition for storing files or can I just make an ordinary disc somehow??I'm not sure what you mean, but you can make another partition and mount it to store files. You mount it on a "mount point" that you create in your Ubuntu file system. A mount point is just a directory. Since you already have a /home directory, you should not mount your storage partition there. Usually, you create a mount point in a /mnt directory, using the mkdir command:```
sudo mkdir /mnt/storage
```Then you mount the partition to the /mnt/storage mount point using the mount command, like this:```
sudo mount /dev/sda5 /mnt/storage
```. That is assuming the storage partition is sda5. If you want it mount automatically at boot time, you can edit the /etc/fstab file an put the mount command in there. The syntax is a little different than the mount command. See the mount man page for more information:```
man mount
```

---

### Post by MuRRe on 2009-02-19
> **dstew said:**
> I'm not sure what you mean, but you can make another partition and mount it to store files. You mount it on a "mount point" that you create in your Ubuntu file system. A mount point is just a directory. Since you already have a /home directory, you should not mount your storage partition there. Usually, you create a mount point in a /mnt directory, using the mkdir command:```
sudo mkdir /mnt/storage
```Then you mount the partition to the /mnt/storage mount point using the mount command, like this:```
sudo mount /dev/sda5 /mnt/storage
```. That is assuming the storage partition is sda5. If you want it mount automatically at boot time, you can edit the /etc/fstab file an put the mount command in there. The syntax is a little different than the mount command. See the mount man page for more information:```
man mount
```

Thanks for the help.

---

