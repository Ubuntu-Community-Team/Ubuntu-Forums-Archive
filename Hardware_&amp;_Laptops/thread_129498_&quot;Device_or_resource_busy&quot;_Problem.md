---
title: "&quot;Device or resource busy&quot; Problem"
date: 2006-02-13
forum: Hardware &amp; Laptops
---

### Post by tiris on 2006-02-13
The background information of this problem is this:
This is a file server that I am trying to install a raid1 array on.
Before installing ubuntu-server on this machine I had gentoo installed on it.
While having gentoo installed on this machine I tried to create a raid array and successfully did, but was unsure how to administer the thing (e.g. what to do when something goes wrong).

I got interested in ubuntu because it seemed easer to setup and deal with in general, but now I don't know how to build the array again.

After installing ubuntu-server on this machine I only installed ssh-server and then tried to build the array.
```

>#sudo fdisk -l /dev/hdb

Disk /dev/hdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       24792   199141708+  fd  Linux raid autodetect

>#sudo fdisk -l /dev/hdc

Disk /dev/hdc: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1       24792   199141708+  fd  Linux raid autodetect

>#cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/Ubuntu-root /               ext3    defaults,errors=remount-ro 0    1
/dev/hda1       /boot           ext3    defaults        0       2
/dev/mapper/Ubuntu-swap_1 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

>#cat /etc/mtab
/dev/mapper/Ubuntu-root / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /dev/shm tmpfs rw 0 0
usbfs /proc/bus/usb usbfs rw 0 0
tmpfs /lib/modules/2.6.12-9-386/volatile tmpfs rw,mode=0755 0 0
/dev/hda1 /boot ext3 rw 0 0
tmpfs /dev tmpfs rw,size=10M,mode=0755 0 0

```


The actions I took during the raid installation that lead to this problem are as follows:

#fdisk dev/hdb
//remove all partitions
//make one partition of the fd type (Linux raid autodetect)
>p
>1
>[enter]
>[enter]
>t
>fd
>w
#fdisk dev/hdc
//remove all partitions
//make one partition of the fd type (Linux raid autodetect)
>p
>1
>[enter]
>[enter]
>t
>fd
>w
#mdadm --create /dev/md0 --level 1 --raid-devices=2 /dev/hdb1 /dev/hdc1

mdadm: Cannot open /dev/hdb1: Device or resource busy
mdadm: Cannot open /dev/hdc1: Device or resource busy
mdadm: create aborted


Any suggestions?

---

### Post by tiris on 2006-02-14
Also if there is more information needed let me know.

---

### Post by tiris on 2006-02-14
The thing that really hangs me up on this problem is that the device reported busy is not supposed to be in use.

Is there a way to track what programs are using a certain device?

---

### Post by tiris on 2006-02-15
```
:~$ sudo /usr/sbin/lsof /dev/hdb1
:~$ sudo /usr/sbin/lsof /dev/hdc1
:~$ sudo /usr/sbin/lsof /dev/md0
:~$ sudo /usr/sbin/lsof | grep hdb1
:~$ sudo /usr/sbin/lsof | grep hdc1
:~$ sudo /usr/sbin/lsof | grep md0
md0_raid1 3048   root  cwd       DIR      253,0    4096          2 /
md0_raid1 3048   root  rtd       DIR      253,0    4096          2 /
md0_raid1 3048   root  txt   unknown                               /proc/3048/exe
```

only the last command had any output???

As an beginner let me guess what this means.
1. I am using the function wrong
2. md0 is being used so it is likely the resource that is busy and not the other drives like I originally thought.

Just for speculative fun.

```
:~$ sudo /usr/sbin/lsof | grep md1
md1_raid1 3073   root  cwd       DIR      253,0    4096          2 /
md1_raid1 3073   root  rtd       DIR      253,0    4096          2 /
md1_raid1 3073   root  txt   unknown                               /proc/3073/exe
:~$ sudo /usr/sbin/lsof | grep md2
:~$ sudo /usr/sbin/lsof | grep md3
:~$ sudo /usr/sbin/lsof | grep md4
```

I would like to thank the people involved with COLUG for the tip on lsof.

---

### Post by tiris on 2006-02-22
Hmm there is not an /etc/raidtab file and yet there are two raid devices that come up on reboot.

I guess this means that the Kernel is loading the raid devices?
or I guess mdadm could be loading them but I have never read anything about that in the documentation.

This is just another clue, I will look into it more later (when I get time).

```
:~$ cat /proc/mdstat
Personalities : [raid1]
md1 : active raid1 hdb1[0] hdc1[1]
      199141632 blocks [2/2] [UU]

md0 : active raid1 hdb[0] hdc[1]
      199148480 blocks [2/2] [UU]

unused devices: <none>
```

---

### Post by SgtPepperKSU on 2006-09-27
Did you ever resolve this?  I am having the **exact** same problem with 6.06.

---

### Post by tiris on 2006-09-27
> **SgtPepperKSU said:**
> Did you ever resolve this?  I am having the **exact** same problem with 6.06.

Yes, I found that mdadm doesn't need the raidtab to operate and so you have to use it to stop using the disks in question.

What was happening was mdadm saw the superblock and automatically loaded them for use with mdadm. 

I think I might have this solution archived on my home machine so if you have trouble reply to this thread and I will look through my files.

---

### Post by SgtPepperKSU on 2006-09-27
Okay, that makes sense.  So, I just need to do:
```
sudo mdadm --stop /dev/md0
sudo mdadm --stop /dev/md1
sudo mdadm --verbose --create /dev/md0 --level raid1 --raid-devices=2 /dev/hda3 /dev/hdb1
```
Right?

I will try this when I get home from work, and will reply either very happy or asking for more details. :D

---

### Post by SgtPepperKSU on 2006-09-27
Thank you! Worked like a charm!
```
[FONT="Courier New"][B]:~$ sudo mdadm --stop /dev/md0
:~$ sudo mdadm --stop /dev/md1
:~$ sudo mdadm --verbose --create /dev/md0 --level raid1 --raid-devices=2 /dev/hda3 /dev/hdb1[/B]
mdadm: /dev/hda3 appears to be part of a raid array:
    level=1 devices=2 ctime=Mon Sep 25 15:20:38 2006
mdadm: /dev/hdb1 appears to be part of a raid array:
    level=1 devices=2 ctime=Mon Sep 25 15:20:38 2006
mdadm: size set to 39061952K
Continue creating array? y
mdadm: array /dev/md0 started.
**:~$ cat /proc/mdstat**
Personalities : [raid1]
md0 : active raid1 hdb1[1] hda3[0]
      39061952 blocks [2/2] [UU]
      [>....................]  resync =  1.4% (572544/39061952) finish=29.1min speed=22020K/sec

unused devices: <none>[/FONT]
```

---

### Post by fmasi on 2006-09-28
I have the same problem aroud but whith ubuntu dapper. The thing is i remember having done it before and it whorked but i did it rong so i have to use:

mdadm --zero-superblock on my sda and sdb

I am using kernel 2.6.17.13 becouse only whith 2.6.27x and up my raid controler is suported.

the output of fdisk -l is:
```

root@fmasi-desktop:~# fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           6       48163+  83  Linux
/dev/sda2               7          68      498015   fd  Linux raid autodetect
/dev/sda3              69       30401   243649822+   5  Extended
/dev/sda5              69         566     4000153+  fd  Linux raid autodetect
/dev/sda6             567       30401   239649606   fd  Linux raid autodetect

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1           6       48163+  83  Linux
/dev/sdb2               7          68      498015   fd  Linux raid autodetect
/dev/sdb3              69       30401   243649822+   5  Extended
/dev/sdb5              69         566     4000153+  fd  Linux raid autodetect
/dev/sdb6             567       30401   239649606   fd  Linux raid autodetect

Disk /dev/hda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3595    28876806    7  HPFS/NTFS
/dev/hda2            3596        4870    10241437+   5  Extended
/dev/hda5            3596        3726     1052226   82  Linux swap / Solaris
/dev/hda6            3727        4870     9189148+  83  Linux
root@fmasi-desktop:~#

```



the output of cat /proc/mdstat is:
```

root@fmasi-desktop:~# cat /proc/mdstat
Personalities :
unused devices: <none>
root@fmasi-desktop:~#

```

the output of /usr/sbin/lsof is:
```

root@fmasi-desktop:~# /usr/sbin/lsof /dev/md0
root@fmasi-desktop:~# /usr/sbin/lsof /dev/md1
root@fmasi-desktop:~# /usr/sbin/lsof /dev/sda2
root@fmasi-desktop:~# /usr/sbin/lsof /dev/sdb2
root@fmasi-desktop:~# /usr/sbin/lsof /dev/sda
root@fmasi-desktop:~# /usr/sbin/lsof /dev/sdb
root@fmasi-desktop:~#

```

the output of /usr/sbin/lsof is:

```

root@fmasi-desktop:~# /usr/sbin/lsof | grep md0
root@fmasi-desktop:~# /usr/sbin/lsof | grep md1
root@fmasi-desktop:~# /usr/sbin/lsof | grep sda
xfsdatad/  164       root  cwd       DIR        3,6    4096          2 /
xfsdatad/  164       root  rtd       DIR        3,6    4096          2 /
xfsdatad/  164       root  txt   unknown                               /proc/164/exe
root@fmasi-desktop:~# /usr/sbin/lsof | grep sda1
root@fmasi-desktop:~# /usr/sbin/lsof | grep sda2
root@fmasi-desktop:~# /usr/sbin/lsof | grep sda3
root@fmasi-desktop:~# /usr/sbin/lsof | grep sda5
root@fmasi-desktop:~# /usr/sbin/lsof | grep sda6
root@fmasi-desktop:~# /usr/sbin/lsof | grep sdb
root@fmasi-desktop:~# /usr/sbin/lsof | grep sdb1
root@fmasi-desktop:~# /usr/sbin/lsof | grep sdb2
root@fmasi-desktop:~# /usr/sbin/lsof | grep sdb3
root@fmasi-desktop:~# /usr/sbin/lsof | grep sdb5
root@fmasi-desktop:~# /usr/sbin/lsof | grep sdb6
root@fmasi-desktop:~#

```

my cat /etc/fstap is:

```

root@fmasi-desktop:~# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
root@fmasi-desktop:~#

```

my /etc/mtab

```

root@fmasi-desktop:~# cat /etc/mtab
/dev/hda6 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
/sys /sys sysfs rw 0 0
varrun /var/run tmpfs rw 0 0
varlock /var/lock tmpfs rw 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
devshm /dev/shm tmpfs rw 0 0
root@fmasi-desktop:~#

```


the only thing whierd i can find is in /usr/sbin/lsof | grep sda it says :

```

root@fmasi-desktop:~# /usr/sbin/lsof | grep sda
xfsdatad/  164       root  cwd       DIR        3,6    4096          2 /
xfsdatad/  164       root  rtd       DIR        3,6    4096          2 /
xfsdatad/  164       root  txt   unknown                               /proc/164/exe
root@fmasi-desktop:~#

```

How to take that off maby its that that is bloking my device.

thx for the help.

[CENTER]Frederic Masi[/CENTER]

---

### Post by SgtPepperKSU on 2006-09-28
> **fmasi said:**
> the only thing whierd i can find is in /usr/sbin/lsof | grep sda it says :

```

root@fmasi-desktop:~# /usr/sbin/lsof | grep sda
xfsdatad/  164       root  cwd       DIR        3,6    4096          2 /
xfsdatad/  164       root  rtd       DIR        3,6    4096          2 /
xfsdatad/  164       root  txt   unknown                               /proc/164/exe
root@fmasi-desktop:~#

```

How to take that off maby its that that is bloking my device.
That grep match looks completely coincidental.  It's just that "xfsdatad" contains the string "sda".  Does your mdadm output show all of your partitions as busy?

---

### Post by tiris on 2006-09-28
*looks blankly at the screen for a moment*

I am not sure I understand the problem so let me restate it.
________________
You tried to recreate a raid array and got some message stating that your “Device or resource busy”(sda and sdb?).
________________

It looks like you are using hda6 to boot so that you can work on the raid array.
Also you stated that you zeroed out the raid superblock.

From what was stated I don't see how what would keep the array from building.

A copy of the console output from trying to create the array would be most useful.

---

### Post by fmasi on 2006-09-28
What i like to do right now is just creting some raid 0 on my 2 sata2 disk /dev/sda and /dev/sdb i dont car about erasing every thing on them cince they never contained any data on them.

I did once try to create a raid but then i changed my myde aboute the partition layout and recriated that new partition layout that you can see in my fdisk -l as listed abouve.

i nead to create one md0 whith /dev/sda2 and /dev/sdb2 
one md1 whith /dev/sda5 and /dev/sdb5 and finaly one md2 whith /dev/sda6 /dev/sdb6.

the /dev/md0 will be my swap the /dev/md1 will be my / and the /dev/md2 will be my /home and i have the /dev/sda1 and /dev/sdb1 as    partitions i not going to use right now. Maby i use some of them as a /boot but just nead the /dev/md0 the /dev/md1 and /dev/md2 to work whith raid0.

As i say i dont car about clening formating repartitioning the hd i can do any thing whith them becuse they are clean (no data on them)


If you have anny idia of what mey be kiping mdadm from creating the array i will be vary hapy to know about it.

---

### Post by SgtPepperKSU on 2006-09-29
Well, let's start by seeing your mdadm command and its output.

---

### Post by fmasi on 2006-10-02
This is my mdadm comand:

```
root@fmasi-desktop:~# mdadm --create --verbose /dev/md0 --level=0 --raid-devices=2 /dev/sda2 /dev/sdb2
mdadm: chunk size defaults to 64K
mdadm: Cannot open /dev/sda2: Device or resource busy
mdadm: Cannot open /dev/sdb2: Device or resource busy
mdadm: create aborted
root@fmasi-desktop:~#
```

I was thinking about all that and it came to my mind that it may be the kernel hat i compiled (sinse i nead 2.6.17 and up) becouse i had alredy done 3 kernels and i remember the first one worked but i dont have it any more. I guess i going to compile a new one to see if it is some thing whith the kernel what do you think?:-k

---

### Post by fmasi on 2006-10-12
Some one please help me i geting desprete whith this 2 sata.

I tryng to recompile kernels etc.. but dosent mather what i do i always have the same error device busy

---

### Post by dccool879 on 2006-10-16
can someone help me with this cookie,
i dive right in:
```
frf@freerideforums:~$ sudo mdadm --create --verbose /dev/md0 --level=1 --raid-de                                             vices=2 /dev/hdc1 /dev/hdd1
mdadm: Cannot open /dev/hdc1: Device or resource busy
mdadm: Cannot open /dev/hdd1: Device or resource busy
mdadm: create aborted

```
shoot...
```
frf@freerideforums:~$ cat /proc/mdstat
Personalities :
unused devices: <none>

```
shouldnt it work if there are no raids here?

then i try to umount my hard drives, but i can only unmount hdd1 because that is what im going to mirror to, i am using hdc1. i get this when only hdc1 is mounted
```
frf@freerideforums:~$ sudo mdadm --create --verbose /dev/md0 --level=1 --raid-devices=2 /dev/hdc1 /dev/hdd1
mdadm: Cannot open /dev/hdc1: Device or resource busy
mdadm: /dev/hdd1 appears to contain an ext2fs file system
    size=19551072K  mtime=Mon Oct 16 21:13:50 2006
mdadm: create aborted

```

can i not raid my mounted drive, which i want to be backed up? how should i go about mirroring hdc1 (my primary partition) to hdd1?
```

frf@freerideforums:~$ sudo fdisk -l /dev/hdc

Disk /dev/hdc: 20.4 GB, 20493656064 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        2398    19261903+  83  Linux
/dev/hdc2            2399        2491      747022+   5  Extended
/dev/hdc5            2399        2491      746991   82  Linux swap / Solaris
frf@freerideforums:~$ sudo fdisk -l /dev/hdd

Disk /dev/hdd: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1        2434    19551073+  83  Linux
frf@freerideforums:~$
```

---

### Post by dccool879 on 2006-10-16
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
# /dev/hdd1       /media/mirrored ext3    defaults,errors=remount-ro 0       1

```

if this helps

---

### Post by dccool879 on 2006-10-18
i'm still stuck : (

---

### Post by dccool879 on 2006-10-18
ok i did it with the live cd and it worked, and upon reboot i got the "device or resource busy" for /dev/hdc1 when i tried to boot. So i had to remove the raid to get the computer to at least boot again. Is this problem maybe caused by the fact /dev/hdd1 is mounted to /media/mirrored ??

---

### Post by dccool879 on 2006-10-22
bump, still stuck :(

---

### Post by predder on 2006-11-08
I had a similar problem and came across this thread via google. Just posting my solution in case anyone has the same half hour headache :(

I had a drive with a fresh install of debian on it. When I plugged in an old drive that was previously in a raid array it was automatically bought up as a raid device at boot time. The problem being that when I tried to stop the raid devices so I could re-create them I got the device or resource busy for one of the partitions even though it wasnt mounted anywhere.

Turns out the OS had automatically recognised one of the partitions was previously a swap partition and enabled it. swapoff /dev/md2 fixed it.

Sorry to see your problem dccool879. If you figure it out make sure you post what you did.

---

### Post by tiris on 2006-11-09
> **dccool879 said:**
> bump, still stuck :(

In Post #20 you said it worked when you used a live cd. This is because you cannot have a partition mounted when you add it to a raid array. In the case of a live CD you are running off of the cd and making a raid array with two unmounted devices.

I am assuming that you are booting from hdc1 and therefor cannot just unmount the device.

I think I saw a solution to this somewhere on the net I will see if I can dig it up for you. I know it has to do with creating a broken array then rebooting and adding the second device. I will get back if I find anything.

---

### Post by tiris on 2006-11-09
Dccool,
I don't know if you still haven't been able to get your raid array up and running but I did find something for you.
[http://www.linux-sxs.org/hardware/raid_for_idiots.html](http://www.linux-sxs.org/hardware/raid_for_idiots.html)
The above link shows how to install raid1 on a system that is running.

Also if you would like to ease the pain of raid I would buy a hardware raid controller. The operation is more straight forward and happens before the operating system so everything will be copied to the other disk including *gasp* a Windows partition. If using a hardware raid controller I would advise using disks of the same size to avoid complications.

---

### Post by dccool879 on 2006-11-23
thanks for the replies. i'm at my grandparents for thanksgiving but i will give my raid another shot when i get back. as far as hardware raid, maybe i should just do this. i wouldnt be surprised if my motherboard already has a raid controller on it. It is a sort of fancy motherboard from the p3 days. if i had a raid controller built into the mobo, would i find it in my BIOS? because i looked there with no luck. also isn't hardware raid way faster?

---

### Post by matthewcraig on 2007-11-14
To follow up again, in case it was not clear to anyone, you will use the --verbose option.  This makes the difference between being able to force the create or just getting an error.

---

### Post by munk on 2008-04-03
Or you could try uninstalling EVMS, which worked in my case.

The symptoms were that I had previously physically removed a RAID member and now wanted to add it back in, but ```
mdadm /dev/mdN -a /dev/sdN
``` was saying that /dev/sdN was busy, despite it not showing up in the output of lsof or fuser.

Doing an ```
apt-get remove evms
``` and rebooting allowed me to hotadd the device back in.

HTH, Andy

---

