---
title: "procedure to increase user space"
date: 2009-01-25
forum: Hardware
---

### Post by shahin on 2009-01-25
Greetings-
   I run Hardy in double boot mode with xp, and lately my applications give me errors about limited space in my user directory.  First audacity, and now evolution.  Would someone please point me to directions to safely allocate more space?  I also appreciate if you can point me documents about how this environment is set up?  ie. Do I need to allocate more space to each folder or just increasing room in /home/user_name will do the trick?

---

### Post by 73ckn797 on 2009-01-25
The space issue is more likely related to the partition size you have designated for Ubuntu. That can be changed by making the XP partition smaller and increasing the Ubuntu partition.

Using a LiveCD, boot up into it from the first option to use without changing your computer.

Go to System/Administration/Partition Editor.

In there select the XP partition and resize it to a smaller size. Allow that to complete. Then you can select the Ubuntu partition and increase the size of it in similar manner. I recommend defragmenting the XP partition prior to making any changes. Back-up important files in case something goes wrong. If you have a lot of Documents in each operating system you may need to move some of those off the computer to a CD or DVD, making a data disk. That depends upon whether you are running out of space on both partitions.

What is the capacity of the hard drive and how much space is used up between both operating systems?

Open terminal and enter:
```
 sudo fdisk -l
```

Reference info:
[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)     "Documentation"

[https://help.ubuntu.com/community/TitleIndex](https://help.ubuntu.com/community/TitleIndex)       "Documentation Index"

Look around in the documentation for further info.

---

### Post by shahin on 2009-01-25
Thanks for the information.  When I right click the file system icon, seems I have allocated 64G, and used only 24.  I believe that is telling me the entire size of the hd.  Is there a command to show me how much is allocated to Ubuntu without booting into the desk top cd environment?  Is there any other commands I should run?

---

### Post by shahin on 2009-01-25
ok I am not looking at the Gparted seems /dev/sda6 is the only partition that is almost full.  It has about 500M in it.  I shrinked the size of windows, and then the space is labled as unallocated.  How do I add this unallocated portion to /dev/sda6 please?  I do not really see a way to increase the size of a partition.
What I can do is to copy /dev/sda6 into the new space.  I have done that.  Am I done now?  Can I delete the old copy of /dev/sda6?  
My HD is devided into 40G for windwos called /dev/sda1.  Then there is the newly allocated space called /dev/sda4 for 20G.  The there is /dev/sda2 which is about 13.71G and only half of it is used and it is ext3, so I do not understand why I had the space porblem to begin with.  I think it is bacause I created different partitions for data and other system resources.  Then there is /dev/sda2 which is composed of a bunch of sub partitions like /dev/sda10, 9, 8, 7,6 and 5.

---

### Post by shahin on 2009-01-25
Here is the result of fdisk -l command you asked me to run
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5223    41953716    7  HPFS/NTFS
/dev/sda2            7843        9632    14378175   83  Linux
/dev/sda3           10275       14593    34692367+   5  Extended
/dev/sda4            5224        7842    21037117+  83  Linux
/dev/sda5           14312       14593     2265133+  82  Linux swap / Solaris
/dev/sda6           13096       14311     9767488+  83  Linux
/dev/sda7           11879       13094     9767488+  83  Linux
/dev/sda8           11270       11877     4883728+  83  Linux
/dev/sda9           10661       11268     4883728+  83  Linux
/dev/sda10          10275       10659     3092449+  83  Linux

Partition table entries are not in disk order
ubuntu@ubuntu:~$ 

Any help is greatly appreciated.

---

### Post by 73ckn797 on 2009-01-25
> **shahin said:**
> ok I am not looking at the Gparted seems /dev/sda6 is the only partition that is almost full.  It has about 500M in it.  I shrinked the size of windows, and then the space is labled as unallocated.  How do I add this unallocated portion to /dev/sda6 please?  I do not really see a way to increase the size of a partition.
What I can do is to copy /dev/sda6 into the new space.  I have done that.  Am I done now?  Can I delete the old copy of /dev/sda6?  
My HD is devided into 40G for windwos called /dev/sda1.  Then there is the newly allocated space called /dev/sda4 for 20G.  The there is /dev/sda2 which is about 13.71G and only half of it is used and it is ext3, so I do not understand why I had the space porblem to begin with.  I think it is bacause I created different partitions for data and other system resources.  Then there is /dev/sda2 which is composed of a bunch of sub partitions like /dev/sda10, 9, 8, 7,6 and 5.


You should be able to just select the Ubuntu partition and with cursor on one end, hold down the left mouse button and drag the end of the partition over into the unallocated space then click apply.

I do not understand how you ended up with so many partitions. A typical installation that I have dealt with would include a Windows partition, Ubuntu and then a small "swap" partition.

---

### Post by shahin on 2009-01-25
-  The reason I have several partitions is for security concerns according to a tutorial that I can share once I log back in to my system.
-  Here is some of the issues I run into: I tried to shrink /dev/sda2 so I can add the extra space to /dev/sda7, and as a result I get an unallocated space.  I can not then format it as new.  I get the following error:
It is not possible to create more than one primary partition.  If you want more partitions you should first create an extended partition. Such a partition can contain other partitions. Because an extended partition is also a primary partition it might be necessary to remove a primary partition first. 
I get this error as soon as I click new.  The software seems to assume I want to create a primary partition.  

As of now, I have a 20G of unallocated space, and a 5G.  But when I highlight /dev/sda6, and then click resize.  There is an arrow on the right hand side which is all the way to the right, and there is really no more space to increase the partition by moving it further to right.  The only partition which I can resize is /dev/sda2, which is the one I shrank a few minutes ago.  
 
Please help.

---

### Post by 73ckn797 on 2009-01-26
No way to increase the partition next to the unallocated space?

My disk space on the laptop dual booting with WinXP is:

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf832f832

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4933    39624291    7  HPFS/NTFS
/dev/sda2            4934        9729    38523870    5  Extended
/dev/sda5            4934        9526    36893241   83  Linux
/dev/sda6            9527        9729     1630566   82  Linux swap / Solaris
```

That is why I cannot believe that you have so many partitions.

There is the NTFS partition, Linux extended, Linux for Ubuntu and the swap partition within the extended partition. That makes things for me completely secure since it is the default structure. I designated partition sizes on installation.

---

### Post by shahin on 2009-01-26
I really do not have any argument regarding the security of 1 vs. several partitions.  I was just sharing that information. What I do know if that my system was working fine, and now I have found a partition that I want to increase but I do not seem to be able to do it.  If you or anyone else can help me with this, I really appreciate it.

---

### Post by estyles on 2009-01-26
Okay, I *think* I understand your problem.  You decreased the size of /dev/sda1, right?  Which is your Windows partition?

Now, you see /dev/sda3?  That is an extended partition, which contains the rest of your "logical" partitions.  So, in order to increase the size of any of your logical partitions, you have to increase /dev/sda3 to take up the rest of the space.  Once you have done that, you'll have to move /dev/sda4 and /dev/sda5 up so that the empty space is next to /dev/sda6.  *Then* you can increase the size of /dev/sda6.  

Note that *moving* a partition (or increasing the size of a partition by adding space to the *beginning* of the partition) can be a bit of a headache - it takes kind of a long time, and if you have any sort of hardware or power failure in the meantime, you may lose data.  It is suggested to backup your data before doing it.

---

### Post by shahin on 2009-01-26
Ok. Thanks for the information.  You are right about what I have done with Windows.  Right before I saw your post, I moved /dev/sda6 by copy/past feature of Gparted into a 10G space.  Now my HD is somewhat fragmented.  But I got more space, and I do not seem to get the errors that I was seeing before.  It was little risky, but it seems to have worked.  Now I just have to move things like you stated to get more space in each partition. Thanks for your support.

---

### Post by 73ckn797 on 2009-01-26
> **estyles said:**
> Okay, I *think* I understand your problem.  You decreased the size of /dev/sda1, right?  Which is your Windows partition?

Now, you see /dev/sda3?  That is an extended partition, which contains the rest of your "logical" partitions.  So, in order to increase the size of any of your logical partitions, you have to increase /dev/sda3 to take up the rest of the space.  Once you have done that, you'll have to move /dev/sda4 and /dev/sda5 up so that the empty space is next to /dev/sda6.  *Then* you can increase the size of /dev/sda6.  

Note that *moving* a partition (or increasing the size of a partition by adding space to the *beginning* of the partition) can be a bit of a headache - it takes kind of a long time, and if you have any sort of hardware or power failure in the meantime, you may lose data.  It is suggested to backup your data before doing it.


This info will probably be your best bet.

If you could open Partition Editor and make a print screen of the panel showing the graphical layout, it could help to "see" what you have.

---

