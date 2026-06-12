---
title: "How to re-mount the partitions on Gutsy?"
date: 2007-10-25
forum: Hardware &amp; Laptops
---

### Post by ROBarber on 2007-10-25
Hello.
I have the following issue: after some problems with my laptop I have to re-install the Ubuntu 7.04 OS. I made this successfully, but with with a little inconvenient. When I had to create the partitions on my hard drive (40 GB), after several attempts without success, i Finally manage to make a first partition of 5 GB for file system and 1.39 GB partition for linux-swap. After upgrading OS to Gutsy  I made another 3 partitions with Partition Manager, one of almost 30 GB and two of 8 MB each. The problem is that, I cant access this partition trough a file browser and this is the text from fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=8797c379-0b6a-4f7d-88b8-e50dc03ee905 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda2
UUID=4dadfebe-f710-4258-a8f7-99ae1e56dda8 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

What should I do to have access to my /dev/hda4 partition?

Thank you

---

### Post by MaximusTG on 2007-10-26
To access that partition, you have to mount it at a mount point.

First you have to decide where you want to mount it. For example, in your home partition. In this example I will create a folder called mystuff in your home folder

```

mkdir ~/mystuff #note that ~ means the home folder of the user issuing the command
sudo mount /dev/hda4 ~/mystuff

```

To make this permanent you have to add this to your /etc/fstab
add the following line:

```

/dev/hda4   /home/yourusername/mystuff   ext3    defaults        0       2

```

And replace /home/yourusername/mystuff with the mount point of your choice. You have to edit /etc/fstab as root! (sudo gedit /etc/fstab)

---

### Post by ROBarber on 2007-10-26
Ok, thank you. It seems that the problem is solved. One more question. I only have on first partition 200 Mb of free space. If I have to make some updates or to download some files that will exceed the free space, those actions will be completed on dev4 by default, or I have to do those manually.

---

### Post by MaximusTG on 2007-10-26
Well, updates probably won't be much of a problem, since they overwrite the old ones, but if you're going to install more programs, you're going to run into problems.. 

If you want to add more space to your root(/)-partition, you have to make free space "to the right" of that partition. 

like so:

```


<rootpartition> <swap> <other partitions>
                            /\
                            ||
                       You have to resize this to enlarge your root partition

```

However, from what I gather from your post, your partitions are a bit screwed up (2 partitions of 8 MB?). It would be better to backup all your data, and repartition (better yet, reinstall) so that your disk looks like this:

<rootpartion><swap><home directory>

NOTE: I am not an expert in this but this should (probably) work. 

What you could do:
Backup your data
boot the live cd, and start Gparted (sudo gparted)
Then, delete all partitions, except your root partition (in your case, /dev/hda1), then resize the root partition to about 10 GB, which should be enough. Then make on big partition from the rest, leaving some space for the swap and format that as ext3. Then make a swap partition from the rest of the space. 
Next, mount your root filesystem somewhere
Open a terminal (still on the live-cd) and type:
mkdir ubunturoot
sudo mount /dev/hda1 ubunturoot
gedit ubunturoot/etc/fstab

then edit your fstab to reflect the changes to your partitions (change the partition mounted as swap to the correct one, and probably the root partition too (I believe you can just replace the UUID's with /dev/hda1,2,3 etc)

Reboot into your Ubuntu system.

Now you have to move your home directory to the new partition.

Follow this guide:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

for more info on partitioning:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

Good luck!

---

### Post by ROBarber on 2007-10-26
Well, I moved entire /home to the other partition, so I have a lot of free space now :). 
thanks a lot :), now I'm happy.:guitar:

---

### Post by ROBarber on 2007-11-02
I was happy but not for a long time ;). I just did a new fresh installation of Feisty and upgraded to Gutsy. The problem of free space on / partition wasn't solved. Anyway, every thing is just fine now.

regards:popcorn:

---

