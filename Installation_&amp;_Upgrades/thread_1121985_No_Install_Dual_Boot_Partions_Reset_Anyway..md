---
title: "No Install Dual Boot Partions Reset Anyway."
date: 2009-04-10
forum: Installation &amp; Upgrades
---

### Post by wbee on 2009-04-10
Hello,

Having played around with Ubuntu 8.10 for about a month,learning how to do what I want it to do,I decided to re install a  Windows XP and Ubuntu 8.10 dual boot.

First,I re installed the XP,taking the hours necessary to download all the updates. The C drive and the D drive took up about 12g,once I got everything loaded,from a 150 g hard drive.

((Before you say it,a dual boot was necessary to keep peace in the family.))

I used a registry cleaner to clean it up and defragged both the C and D drives.

Then,I inserted the OS disk,set it to boot from the optical drive,and did.

I went through language,time zone,and typewriter,finally coming to the partition page. The guided-re size partitions dot was filled in as the default.

The top horizontal tube graph showed from left to right,a 2 g spacer,my 12 g of XP,and the representation of roughly 135g of free space.

The next horizontal tube graph showed 13.5 percent for XP and the rest allotted to Ubuntu. **There was no slider,as there was the first time I installed. 

I checked,there was no slider for "contiguous" either. The only option using "contiguous" was a one hundred percent Ubuntu install.

I went forward out of the box,thinking that might get me to the slider window,with the button still on guided re size.

Instead,if brought up a screen asking me to wait while it moved the partitions,telling me that I could change them. It never got above the "0%" setting and the stopped,saying there was a reading error. I was given no opportunity to change anything.

So,I "quit" the install and shut down,(remove cd,enter,shut down).

I rebooted the computer and it checked my XP files for corruption and finally opened the XP program.

There was an icon on the system tray,telling me my hard drive was almost used up.

Without installing the OS or changing the grub,it had allocated the space and I do NOT have the OS installed but I only have a gig and a half left on my hard drive,because Ubuntu allocated it.

Yes,it was the same disk that passed a hash check and correctly installed it before,on the same computer.

--How do I get the hard drive space back into my XP system?

--How do I install so I get the slider, to allocate my hard disk roughly fifty/fifty to each operating system?

Just when I think I have a handle on ubuntu,something like this happens.

-----------

Thank you.

---

### Post by meierfra. on 2009-04-10
Boot from the LiveCD, open a terminal and post the output of

```
sudo fdisk -lu
```

Also download the [testdisk-6.10.linux26.tar.bz2 package](http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2) to your desktop, and then do:

```


cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static  /dev/sda

```

After starting testdisk with the above command, choose
"Proceed",
"Intel",
"Analyze",
"Quick search",
Press "Y" (to search for Vista partitions)
Press "Enter" to continue,
select "Deeper Search" (so it does a deeper search, which could take a while)

Please post the output of the screen that has the deep search results. Also, use your up/down arrow keys to select each partition listed in the deep search results, and press "p" to get a directory listing; please let me know exactly which partitions give you a directory listing.

---

### Post by wbee on 2009-04-10
meierfra,

I have XP,not Vista,does the "y" instruction still apply?

---

### Post by meierfra. on 2009-04-10
Sorry,  press "N" .

---

### Post by wbee on 2009-04-10
meierfra,

Thank you for the help.

Here is the first output result that you requested:


```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x14cb14cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *     9157050    27053459     8948205    7  HPFS/NTFS
/dev/sda2              63     9157049     4578493+   b  W95 FAT32

Partition table entries are not in disk order
```

Here is the output from the "deep search" page:

```
Disk /dev/sda - 160 GB / 149 GiB - CHS 19457 255 63
     Partition               Start        End    Size in sectors
* FAT32                    0   1  1   569 254 63    9156987 [RECOVERY]
D HPFS - NTFS            570   0  1  1683 254 63   17896410
D HPFS - NTFS            570   0  1 10116 254 63  153372555
D HPFS - NTFS            570   0  1 19455 254 63  303403590
D HPFS - NTFS            570   0 10  1683 254 63   17896401
D HPFS - NTFS            622   0  1 10299 254 63  155477070
D HPFS - NTFS            622   0 11 16072 254 63  248220305
D Linux                16073   1  1 19310 254 63   52018407
D Linux Swap           19311   1  1 19456 254 63    2345427

```

And finally,from the immediate previous group,the lines that returned directories:

```
* FAT32                    0   1  1   569 254 63    9156987 [RECOVERY]
D HPFS - NTFS            570   0  1  1683 254 63   17896410
D HPFS - NTFS            570   0  1 19455 254 63  303403590
D Linux                16073   1  1 19310 254 63   52018407
```



---------------

W

---

### Post by meierfra. on 2009-04-10
> The C drive and the D drive took up about 12g,
I assume the C drive was your main XP partition. 
 What was the D drive?  The recovery partition? 
Were the C and D drive each 12g?  Or together?
Did you lose any Data? 

The only partitions you currently have is a  4g recovery partition and  8g Windows partition.  It seems that testdisk did not find any extra  partitions which are worth  recovering.

I suggest to use gparted (the partitioning editor) from the Live CD  to partition your hard drive before you install Ubuntu:

1. Increase the size of the Windows partition to your liking.

2. Use the remaining unallocated space to create an extended partition.

3. Create a logical ext3 partition  partition leaving enough space for a swap partition.

4.  Create a swap partition. Size : about 1.5 times your ram. But, if you don't use hibernation, not more than 2g.

You might also create an extra logical ntfs partition for sharing data between XP and Ubuntu.


After you partitioned the  hard drive, make sure that you can boot into Windows.   Windows should  run an automatic file system check. 
Then install Ubuntu. But choose  manual partitioning instead of one of the guided options.

  Let me know  if you need more detailed instruction.

---

### Post by wbee on 2009-04-10
meierfra,

If I don't reply for a day or two,it will be because of my schedule.

Since I have never used gparted before,I'm going to at least read the manual first so I'm not completely lost.:-)

I can use all the detailed instruction I can get.

The C drive is the main XP partition,about eight g. The D drive is the recovery and boot partition for XP,about four g. Both together are about 12 g.

I'd like to split the drive about fifty/fifty for XP and either Ubuntu or Linux Mint(again,a family thing.)

The computer has 1024 RAM and I don't hibernate. I can keep the systems separate.

-----------

Thanks,

W

---

### Post by meierfra. on 2009-04-10
> I can use all the detailed instruction I can get.

Here are a few tutorials to look at:

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

[http://www.bleepingcomputer.com/tutorials/index.php?act=print&tut=152&client=printer](http://www.bleepingcomputer.com/tutorials/index.php?act=print&tut=152&client=printer)

[http://mywebsite.bigpond.net.au/dfelderh/p23.html](http://mywebsite.bigpond.net.au/dfelderh/p23.html)


> The computer has 1024 RAM and I don't hibernate.

So I recommend a  1.5GB swap partition.

---

### Post by wbee on 2009-04-11
meierfra and all,

Before I actually do anything,let me run this by you:

--Do I read "psycho's" essay correctly that if I set up an ntfs partition,an ext3 partition,an ext3/home partition,and a swap partition,that I can keep my records in the ext3/home partition and access them with XP(should the need ever arise) with the freeware he links AND be able to do a clean install of 11.x when the time comes without losing any records?

--Should I worry (or even care) about flags or will the grub give me the option of which system to enter based upon defaults that Ubuntu or Linux Mint will select at the install?

--I'm not going to do it right now,because I'm tired. But does this sound about right,before I proceed?:


150g hard drive,1028 memory:

5g ntfs recovery
20g ntfs 
100g ext3/home
20g ext3
3g swap

Should I reboot after each partition setting?

--------

Thanks
W

**edit** About five minutes ago,I went into the partition software and changed the 12g file to 20g. When I tried to change the 4g file,it would not let me,and it was fat instead of ntrs.  

But it booted into windows correctly and the petition I worked on was recognized and all is well,so should I leave well enough alone.?

---

### Post by meierfra. on 2009-04-11
> if I set up an ntfs partition,an ext3 partition,an ext3/home partition,and a swap partition,that I can keep my records in the ext3/home partition and access them with XP(should the need ever arise) with the freeware he links 
Accessing an ext3 partition  from XP is a little bit problematic.  There  is a  very stable driver ([Ext2IFS)]("http://www.fs-driver.org/"), but it does not work with the new version of ext3 used by Ubuntu. There is a driver ([ext2fs]("http://sourceforge.net/projects/ext2fsd")) which works with the new ext3, but is not quite as stable as ext3ifs.

So for sharing files with XP  I recommend to use a Data partition formated as ntfs.

> AND be able to do a clean install of 11.x when the time comes without losing any records?
True.  
> 150g hard drive,1028 memory:

5g ntfs recovery
20g ntfs
100g ext3/home
20g ext3
3g swap

....

When I tried to change the 4g file,it would not let me,and it was fat instead of ntrs. 

There is no reason to increase the size of the recovery partition. So just leave it as it is.

Unless you plan on upgrading  your memory, 3GB is too much for the swap partition. I bet you will never use more than 1GB of swap. So 1.5-2 GB should be plenty for swap.

Depending on how much sharing you plan to do between XP and  Ubuntu,  you might want to replace your home partition by an ntfs Data partition. Or you use  both (home and Data)


> Should I reboot after each partition setting?

No.  Resizing the XP partition was the only delicate step. All the remaining partitioning will be quick and harmless. No rebooting required.

---

### Post by wbee on 2009-04-11
meierfra,

Since I have never done this before,since backing up stuff to put in 11.xx when it shows is not that big a deal,here is what I did:

I left the fat32 partition exactly as it was.

I increased the ntfs partition to about 60g.
I created an ext3 partition of about 60g.

I created a linux swap partition of just over 2g

((I decided against putting in an additional fat32 to share data.))

All is well,I got back into XP with no problem at all after it did a disk check.

Now,I went to the install,went to manual,and made sure that everything conformed to the fat,ntfs,ext3,and linuxswap labels,and entered next.

A screen came up that said:

"Root file system is not defined. Please correct from the partition menu."

Having no idea what to do at that point,I backed out of the install,and came here.

So,how and where do I define the root file?

-------

Thanks.

---

### Post by wbee on 2009-04-11
Re: No Install Dual Boot Partions Reset Anyway.
meierfra,

Since I have never done this before,since backing up stuff to put in 11.xx when it shows is not that big a deal,here is what I did:

I left the fat32 partition exactly as it was.

I increased the ntfs partition to about 60g.
I created an ext3 partition of about 60g.

I created a linux swap partition of just over 2g

((I decided against putting in an additional fat32 to share data.))

All is well,I got back into XP with no problem at all after it did a disk check.

Now,I went to the install,went to manual,and made sure that everything conformed to the fat,ntfs,ext3,and linuxswap labels,and entered next.

A screen came up that said:

"Root file system is not defined. Please correct from the partition menu."

Having no idea what to do at that point,I backed out of the install,and came here.

So,how and where do I define the root file?

-------

Thanks.

---

### Post by meierfra. on 2009-04-11
> (I decided against putting in an additional fat32 to share data.))
Good.  If you want a partition for sharing, use NTFS not Fat.


> left the fat32 partition exactly as it was.

I increased the ntfs partition to about 60g.
I created an ext3 partition of about 60g.

I created a linux swap partition of just over 2g
So you decide against a Data and against a Home partition? 
That's fine.  Having less partitions means that you are less likely to run out have space.


> "Root file system is not defined. Please correct from the partition menu."

At the "preparing partition" screen:
select the ext3 partition.
Click on "edit partition".
Set "Use as" to "ext3 journaling file system"
Set the Mount Point to "/"
(Setting the MountPoint to "/" defines the ext3 partition to be the Root file system)

If you want to be able to access your Window partition from Ubuntu, you should also choose a mount point for your Windows partition. For example "/media/XP".

---

### Post by wbee on 2009-04-11
meierfra,


Thank you so much. Everything is working perfectly.

Your help was professional and correct.

-------------
W

---

### Post by meierfra. on 2009-04-11
> Everything is working perfectly.
Great. Have fun with XP and Ubuntu.

---

