---
title: "Partition question in Ubuntu 8.04"
date: 2008-09-10
forum: General Help
---

### Post by smhoward2 on 2008-09-10
hello all, and thanks in advance for all your responses.

I just recently installed ubuntu on a computer that i hope to set up to share files over my home network (2 windows vista computers will connect)
I would like to be able to give my shared files read and write priviliges (thats not real important, so i will get to that when the time comes)

My current setup is so (according to gparted):
I have 1 250gb SATA drive.
/dev/sda1  ext3  /       15gb  boot
/dev/sda3  ext3  /home   20gb
/dev/sda4  ext3          195gb
/dev/sda2  extended      2.89gb  
/dev/sda5  swap          2.89gb

what i would like to do is make sda4 just a partition for data (mp3's and some videos) that i can set for sharing on my network. When i access the volume in ubuntu, it calls it 205gb media and mounts it, but i cannot do anything with it, i would like to create some folders and copy items to it, but somewhere along the line i didn't do something right....I originally had that partition combined with my home partition, but i believe i wouldn't be able to share it with write access on my home network without difficulty so i can copy items from my windows computers.  So i ran the partition manager from a live cd and resized the /home partition and created a new partition with the leftover space and that's  where im at now....thanks for reading this far..
I'd like to let you all know that i'm not real familiar with command line things in linux just yet, so if i can stay away from that, i'd like to, if not, then so be it i will try :)

thanks again for reading!
and if i posted in the wrong place I apologize.

---

### Post by louieb on 2008-09-10
I like your partition setup. 
1st thing I would do is give the partition a meaningful name. You can use 
```
 e2label device [ new-label ]

```or if you really want to stay away from the cli you can used GParted v3.7 (available on the  [SystemRescueCd]("http://www.sysresccd.org/Main_Page") ) or higher - right click on the partition and give the partition a name (label) that way.

Now to share the partition. Open up Nautilus  open the /media folder, right click on  data partitions folder and choose sharing options.  
Should be able to setup the  network share there.

Good Luck.

---

### Post by kpkeerthi on 2008-09-10
You need to mount the partition before you save files in it:

1. Create a folder where you want /dev/sda4 mounted
```
sudo mkdir /media/Shared
```

2. Open /etc/fstab
```
gksudo gedit /etc/fstab
```

3. Add the below line to the end of this file
```
/dev/sda4    /media/Shared    ext3    defaults    0    0
```

4. Save and Exit.

5. Mount the partition you just added
```
sudo mount -a
```
You should now see a shortcut on your desktop. If not, stop here and post back the errors.

6. Since it is an ext3 partition, you would need to change the ownership of the mounted folder to yourself:
```
sudo chown -R <insert-your-user-id-here>:<insert-your-user-id-here> /media/Shared
```
**E.g. **```
sudo chown -R john:john /media/Shared
```
```
sudo chmod -R 755 /media/Shared
```

**Note: **The partition should auto mount next time you reboot with all the permissions intact.

---

