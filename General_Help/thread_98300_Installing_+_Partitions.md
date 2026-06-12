---
title: "Installing + Partitions"
date: 2005-12-02
forum: General Help
---

### Post by Speedyz2 on 2005-12-02
Hello,
   I recently picked up Linux and Kubuntu to start with and have loved it. I was told, however, that it's a good diea to have 3 partitions instead of two. So I was wondering how should I reinstall it with the new partitions. I planned on reinstalling anyway, so I do not need to repartition it as it is. I know you need a / partition and a swap partition, and now I am told that a /home partition is good also. 

I'm mainly wondering if(when you are installing Kubuntu 5.10) there is an option to do this. I was able toget an option up once, that allowed me to choose desktop/home pc/and one other choice, when aprtitions and then it set up the partitions...but no matter what I try I cannot get this option back up. When I chose Desktop it did the 3 partitions, but hung while instlaling so when I went back the partitions were erased and only had 2. / and swap. does anyone know how tog et that option backup during installation?

If not, what size should I make the 3 different partitions....I have a 60Gb drive, with ONLY Linux being run on it.

I know the / partition has to be bootable and NOT logical, but the other option. Does the /home partition have to be logical or no? And is it made AFTEr the SWAP partition or no?

Sorry for all the questions guys, but Thanks for any replies...

---

### Post by amohanty on 2005-12-02
While installing, when it gets to disk partitions there should be an option that says something like "Start manual partition..." 

I would suggest four partitions:
/boot - 50M (it typically uses ~ 14M, but you should allow for upgrades of kernels)
swap - 3x amount of RAM (system memory)
/home - whatever you like based on how you intend to use the machine
/        - rest available (should not be too small - I would suggest at least 5Gs)

For the 60 G drive here would be my suggestions:
Just format the entire drive first using fdisk or some other tool. I typically use a Win98SE boot disk from bootdisk.de

/boot     50M  (bootable - required)
swap     3x times RAM (select the file system type to swap when creating partition)
/home   40G
/             rest


HTH
AM

---

### Post by Qrk on 2005-12-02
When you install it again and get to the partition menu, choose the custom partitioning (or is it manual partitioning?)

You'll be greeted with a list of partions on your harddrive. Delete the partitions you don't want to keep, like your old ubuntu ones. 

Then select the free space, and make a new partition, say 10 GB. Tell the system to mount this as / You don't need any more than 10 GB, really 5 would do the trick. 

I'd format the rest as /home, minus however much swap you need.

---

### Post by Speedyz2 on 2005-12-03
Hey guys,
   Thanks for the input. does the /home partition have to be logical or primary? i know the / partition is primary but wasnt sure on the /home one? thanks for the input though it's really appreciated.

---

### Post by mlomker on 2005-12-03
Mine is in an extended partition:

```

mlomker@mlomkernote:/etc/X11$ sudo fdisk -l

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1216     9767488+  83  Linux
/dev/hda2            1217        7296    48837600    5  Extended
/dev/hda5            1217        7112    47359588+  83  Linux
/dev/hda6            7113        7296     1477948+  82  Linux swap / Solaris

```

---

### Post by amohanty on 2005-12-03
Mines extended too:

fdisk o/p:

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3916    31455238+   7  HPFS/NTFS
/dev/sda2   *        3917        3922       48195   83  Linux
/dev/sda3            3923        9729    46644727+  83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161    5  Extended
/dev/sdb5               1         486     3903732   82  Linux swap / Solaris
/dev/sdb6             487        9729    74244366   83  Linux

```

---

