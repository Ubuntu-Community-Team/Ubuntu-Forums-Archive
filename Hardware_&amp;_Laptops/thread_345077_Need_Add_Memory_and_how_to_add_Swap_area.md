---
title: "Need Add Memory and how to add Swap area"
date: 2007-01-23
forum: Hardware &amp; Laptops
---

### Post by moonhk on 2007-01-23
Hi Reader

Below is my spare PC top list. Do you think my space PC need some memory ?
Currently, 
1.5 GHz CPU
256 RAM 


How to Add Swap in linux ?

moonhk@hex:~$ top

top - 09:32:47 up 22 min,  2 users,  load average: 0.24, 0.21, 0.25
Tasks:  91 total,   1 running,  90 sleeping,   0 stopped,   0 zombie
Cpu(s): 18.6% us,  1.7% sy,  0.0% ni, 68.4% id, 10.6% wa,  0.7% hi,  0.0% si
Mem:    223548k total,   221224k used,     2324k free,     3540k buffers
Swap:        0k total,        0k used,        0k free,    86288k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 4373 root      15   0 55168  11m 4460 S 10.6  5.3   0:46.03 Xorg
 6145 moonhk    15   0 46072  13m 8724 S  9.6  6.4   0:01.31 gnome-terminal
 5174 moonhk    16   0 45924 7400 5860 S  0.3  3.3   0:00.49 gnome-cups-icon
 5742 moonhk    16   0 29932 8648 5256 S  0.3  3.9   0:00.66 notification-da
    1 root      16   0  1564  524  456 S  0.0  0.2   0:01.65 init

---

### Post by kidders on 2007-01-23
Hi there,

Unfortunately, a snapshot of the output of "top" tells you nothing useful about whether you need more RAM. The one thing it *does* appear to indicate is that your PC hadn't touched it swap space since the previous boot. (Linux almost never de-allocates swap it doesn't require for another purpose, so 0k used almost implies 0k used ... ever!)

Long story short: It's hard to tell from what little info. you provided, but what you did post seems to suggest that you don't need any more RAM.

To answer your question though, adding more swap is easy: Create a partition, mkswap it, and add it to your /etc/fstab.

Hope that helps.

**Edit:** I've just noticed that you're using 0k of swap because you don't have any! (Oops!) You *_definitely_* need to correct that. Also, I hope that "10% wa" isn't a typical value, while your PC is resting.

---

### Post by moonhk on 2007-01-23
Thank. added swap area.

moonhk@hex:~$ top


top - 10:59:37 up 7 min,  2 users,  load average: 0.31, 0.55, 0.28
Tasks:  93 total,   1 running,  90 sleeping,   2 stopped,   0 zombie
Cpu(s):  6.0% us,  0.7% sy,  0.0% ni, 91.0% id,  2.3% wa,  0.0% hi,  0.0% si
Mem:    223548k total,   168192k used,    55356k free,     3448k buffers
Swap:   650592k total,    13284k used,   637308k free,    63080k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 4372 root      15   0 53552  10m 4944 S  4.6  4.9   0:20.48 Xorg
 5221 moonhk    15   0 54144  14m 9264 S  1.0  6.8   0:03.17 gnome-terminal
 5149 moonhk    15   0 37332  13m 9404 S  0.7  6.4   0:02.13 gnome-panel
 5144 moonhk    15   0 14252 7772 5816 S  0.3  3.5   0:02.20 metacity
    1 root      16   0  1468  472  412 S  0.0  0.2   0:01.67 init
    2 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0

---

### Post by kidders on 2007-01-23
Hey again,

That looks a bit healthier! :-)

Although it's hard to say what your personal needs might be, 256MB RAM is a little on the low side for most purposes. If you find there's a lot of swapping going on, getting some more RAM might boost performance a bit. Since you called the PC a "spare" box though, perhaps you don't care if it's a bit sluggish. You certainly don't absolutely _have_ to get more. :-)

---

### Post by drahmad on 2007-01-24
***n00b warning***

I just finished xubuntu installation on a Celeron 400Mhz with 64Mb using the low mem mode.

I have a 6.4Gb HDD, and tried to manually set up the partitions during setup (as I wanted to have a larger swap partition).

The settings I had were a 5.4Gb primary bootable partition, and with the rest of the space I changed the setting to "swap file".

1. I think the file system set up with "ext3" file system - was this the correct option?

2. I can't seem to use the "file manager" to check if I have another partition - it just doesn't seem to be there in the list? Why can't I see the drives/partitions as I'm used to in Windows?

3. When I typed "top" into terminal, I got this:

up 1:21 2 users, load average: 0.39, 0.43, 0.44
Tasks: 73 total, 1 running, 72 sleeping, 0 stopped, 0 zombie
Cpu(s) 2.3%us, 1.0%sy, 0.0%ni, 96.0%id, 2.6%wa, 0.0%hi, 0.0%si, 0.0%s
Mem: 61064 total, 58564k used, 2500k free, 1692k buffers
Swap: 963860k total, 49680k used, 914180k free, 23360k cached

What does this tell you? Does this mean I have a properly working swap partition?

---

### Post by moonhk on 2007-01-24
try vmstat , try to load heavy application. check swap so value. 

below is my machine swap value.

   Swap
       si: Amount of memory swapped in from disk (/s).
       so: Amount of memory swapped to disk (/s).



moonhk@hex:~/javaux/mail$ vmstat -n 5
procs -----------memory---------- ---swap-- -----io---- --system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in    cs us sy id wa
 2  0  23916   3696   2708  66076    2    8    88    25  220   532 17  2 79  2
 0  0  23916   3528   2716  66068    0    0     0     8  246   477 16  1 83  0
 0  0  23916   9028   2728  65720   13    0    67     0  325   568 17  2 81  1
 0  0  23916   9124   2740  65776    0    0     0    39  154   251  2  0 98  0
 0  0  23916   5276   2888  67908  333    0   791    37  277   530 11  2 63 24
 0  2  23916   2088   2008  67160   13    0  1078    36  221   378 11  2 62 25
 0  1  28740   2196   1316  62900    0  945  2122  1076  234   633 27  5  0 68
 0  1  42240   2644   1368  61960    0 2713   830  2746  271   703 37  8  0 55
 0  2  58544   2212   1076  75020    6 3270  4091  3313  257   425 15  3  0 82
 0  1  78780  49368   1096  73440   51 4008   623  4083  192   494 21 30  0 49
 0  0  78768  43528   1804  75332  122    0   529    67  172   501 13  2 62 23
 0  0  78768  43468   1804  75332    0    0     1     0  238   526  5  1 94  0

moonhk@hex:~/javaux/mail$

**try fdisk to print the print the partition table**.

root@hex:~# fdisk /dev/hda

The number of cylinders for this disk is set to 2501.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): m
Command action
   a   toggle a bootable flag
   b   edit bsd disklabel
   c   toggle the dos compatibility flag
   d   delete a partition
   l   list known partition types
   m   print this menu
   n   add a new partition
   o   create a new empty DOS partition table
   p   print the partition table
   q   quit without saving changes
   s   create a new empty Sun disklabel
   t   change a partition's system id
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit
   x   extra functionality (experts only)

Command (m for help): p

Disk /dev/hda: 20.5 GB, 20576747520 bytes
255 heads, 63 sectors/track, 2501 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2414    19390423+  83  Linux
/dev/hda2            2415        2495      650632+   5  Extended
/dev/hda5            2415        2495      650601   82  Linux swap / Solaris

Command (m for help):

**check /etc/fstab hav swap device or not **

root@hex:/etc# cat fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
**/dev/hda5       none            swap    sw              0       0**
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1       /mnt/backup     vfat iocharset=utf8,umask=000 0 0
/dev/hdb1       /mnt/disk2      ext2  defaults 0 0

root@hex:/etc#

---

### Post by moonhk on 2007-01-24
I think I need to add 512MB to my space PC. When running eclipse about 200MB memory in swap area.


moonhk@hex:~$ top

top - 09:57:01 up 43 min,  3 users,  load average: 0.99, 0.80, 0.59
Tasks:  95 total,   1 running,  93 sleeping,   1 stopped,   0 zombie
Cpu(s): 10.0% us,  3.0% sy,  0.0% ni, 80.7% id,  6.0% wa,  0.3% hi,  0.0% si
Mem:    223548k total,   147368k used,    76180k free,     1260k buffers
Swap:   650592k total,   201812k used,   448780k free,    87156k cached

---

### Post by kidders on 2007-01-25
Yeah,

Thinking about that particular example in crude, simplistic terms, imagine you're actually *using* eclipse (ie it switches from being a background task to being the active application). That 200MB will need to be swapped into RAM, leaving you with 50 or 60 MB of "real" memory to do everything else your machine might want to do while eclipse is running. The result is a PC that _has_ to swap before it can do anything at all, which you can see happening when you run "top".

[LIST=1]
[*]Open top, hit 'S' and set a 0.5 - 1.0 second update interval.
[*]Leave it sit in the corner of your screen and do some stuff.
[*]Keep an eye on the %wa indicator.
[/LIST]

This is essentially the percentage of your CPU time being wasted while your box **wa**its for I/O operations to complete. Obviously I/O to swap is hundreds of times slower than I/O to RAM, so you should see this percentage go up higher (and for longer) than you would like.

Of course, in practical terms, there are things you can do in the short term, to curtail your RAM requirements, before you buy more of it. For instance, you might like to try a lightweight desktop environment, such as Xfce, enlightenment, etc.

Imo, you should definitely add that extra 512k, but you might feel better about spending all that money if you can actually *see* why you need it. Hopefully that was of some help. :-)

---

