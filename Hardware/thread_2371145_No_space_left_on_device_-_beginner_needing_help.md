---
title: "No space left on device - beginner needing help"
date: 2017-09-11
forum: Hardware
---

### Post by Grant_Williamson on 2017-09-11
Hi
I'm on 16.04. I'm a beginner at all things Ubuntu and computers, with a small budget, Sorry for that... just trying my best. 
There is history to this - I had a faulty drive, so I bought and installed a 1TB internal hard drive.
I then searched for help on this forum on how to partition the new drive and create a new boot partition, which I thought I did brilliantly, I can now boot my computer (16.04) but alas I cannot do anything else, I have "no space left on device" errors every time i try install something as well as a "no-entry" icon in my status bar which says "Error broken count >0"  

I've searched for help, but cannot follow the advanced instructions. From what I can see, this might help:
```

xyz:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            1.9G     0  1.9G   0% /dev
tmpfs           385M  6.0M  379M   2% /run
/dev/sda2       6.7G  6.6G     0 100% /
tmpfs           1.9G   18M  1.9G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           1.9G     0  1.9G   0% /sys/fs/cgroup
/dev/loop1      232M  232M     0 100% /snap/vuze-vs/2
/dev/loop0       82M   82M     0 100% /snap/core/2774
/dev/loop2       81M   81M     0 100% /snap/core/2462
tmpfs           385M   28K  385M   1% /run/user/1000
/dev/sda1       911G  763G  101G  89% /media/grantwiley/8c2fb140-27e1-4512-84ab-334bbde5a7f8
```



and 

```
:~$ dpkg -l | grep linux-image-
ii  linux-image-4.10.0-32-generic               4.10.0-32.36~16.04.1                          amd64        Linux kernel image for version 4.10.0 on 64 bit x86 SMP
iU  linux-image-4.10.0-33-generic               4.10.0-33.37~16.04.1                          amd64        Linux kernel image for version 4.10.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-87-generic                4.4.0-87.110                                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-92-generic                4.4.0-92.115                                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-4.4.0-93-generic                4.4.0-93.116                                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.8.0-36-generic                4.8.0-36.36~16.04.1                           amd64        Linux kernel image for version 4.8.0 on 64 bit x86 SMP
ii  linux-image-extra-4.10.0-32-generic         4.10.0-32.36~16.04.1                          amd64        Linux kernel extra modules for version 4.10.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-87-generic          4.4.0-87.110                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-92-generic          4.4.0-92.115                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-extra-4.4.0-93-generic          4.4.0-93.116                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.8.0-36-generic          4.8.0-36.36~16.04.1                           amd64        Linux kernel extra modules for version 4.8.0 on 64 bit x86 SMP
iU  linux-image-generic                         4.4.0.93.98                                   amd64        Generic Linux kernel image
iU  linux-image-generic-hwe-16.04               4.10.0.33.35                                  amd64        Generic Linux kernel image

```
and

```
:~$ df -i
Filesystem       Inodes  IUsed    IFree IUse% Mounted on
udev             486194    501   485693    1% /dev
tmpfs            491764    683   491081    1% /run
/dev/sda2        440000 336803   103197   77% /
tmpfs            491764     34   491730    1% /dev/shm
tmpfs            491764      5   491759    1% /run/lock
tmpfs            491764     16   491748    1% /sys/fs/cgroup
/dev/loop1        33000  33000        0  100% /snap/vuze-vs/2
/dev/loop0        13708  13708        0  100% /snap/core/2774
/dev/loop2        13690  13690        0  100% /snap/core/2462
tmpfs            491764     22   491742    1% /run/user/1000
/dev/sda1      60604416  58315 60546101    1% /media/grantwiley/8c2fb140-27e1-4512-84ab-334bbde5a7f8
```

and 

```
:~$ du -h --max-depth=1 | sort -hr
34M    .
25M    ./.cache
5.9M    ./.mozilla
2.3M    ./.config
952K    ./.local
36K    ./.pki
20K    ./.compiz
8.0K    ./.gnupg
4.0K    ./Videos
4.0K    ./Templates
4.0K    ./Public
4.0K    ./Pictures
4.0K    ./Music
4.0K    ./.gconf
4.0K    ./Downloads
4.0K    ./Documents
4.0K    ./Desktop
```

```
:~$ df -h /usr
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2       6.7G  6.6G     0 100% /
```

Totally clueless, so please help if you are wiling to deal with a non-linux person who is just trying to get around having to not pay Gates yet more dollars... thanks in advance!!!

---

### Post by deadflowr on 2017-09-11
Your install is too small.
Minimum should be 8GB.
You only setup 6.7GB.
Now you could clear out some old linux kernels, and free up a little extra space by running 
```
sudo apt-get clean
```
but you're just going to keep running into this problem, repeatedly.

Best to setup a fresh install and set a bigger partition size.

---

### Post by Grant_Williamson on 2017-09-11
> **deadflowr said:**
> Your install is too small.
Minimum should be 8GB.
You only setup 6.7GB.
Now you could clear out some old linux kernels, and free up a little extra space by running 
but you're just going to keep running into this problem, repeatedly.

Best to setup a fresh install and set a bigger partition size.

Thanks. As I said I'm a beginner. 
So:
```
sudo apt-get clean
```
--> Done

Best to setup a fresh install and set a bigger partition size
--> Um... sorry, how?

I know have a bit of free space on the drive, so why is it saying I have no space? i.e.If I bought and installed a new hard drive, it would still say the same thing right? So why do I get this error? And how do I get the system to recognize the free space that I do have (or might have if I installed another new hard drive)?

---

### Post by deadflowr on 2017-09-11
> I know have a bit of free space on the drive, so why is it saying I have no space? i.e.If I bought and installed a new hard drive, it would still say the same thing right? So why do I get this error? And how do I get the system to recognize the free space that I do have (or might have if I installed another new hard drive)?

```
/dev/sda2       6.7G  6.6G     0 100% /
```
this is the only part that matters, as far as the system is concerned.

You'll need to take some space from the /dev/sda1 partition and add it to the /dev/sda2 partition.

Some basic gparted how to's on moving around partition sizes:
[https://gparted.org/display-doc.php%3Fname%3Dmoving-space-between-partitions]("https://gparted.org/display-doc.php%3Fname%3Dmoving-space-between-partitions")

The Ubuntu installation media contains gparted, you can use it in the Try Ubuntu option.

You might want to load the installer Try Ubuntu and take a screen shot of gparted's window and post it in this thread so it would be easier to understand the current partition layout.
And then we should know best way to move things around.

---

### Post by Grant_Williamson on 2017-09-11
So I thought looking at GParted might help... but:

sudo apt install gparted
[sudo] password for grantwiley: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 gparted : Depends: libgtkmm-2.4-1v5 (>= 1:2.24.0) but it is not going to be installed
           Depends: libparted-fs-resize0 (>= 3.1) but it is not going to be installed
 linux-headers-4.10.0-33-generic : Depends: linux-headers-4.10.0-33 but it is not going to be installed
 linux-image-generic-hwe-16.04 : Depends: linux-image-extra-4.10.0-33-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

and then:

:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?


No clue what is going on...

---

### Post by Grant_Williamson on 2017-09-11
> 
You might want to load the installer Try Ubuntu and take a screen shot of gparted's window and post it in this thread so it would be easier to understand the current partition layout.
And then we should know best way to move things around.

Will do...

---

### Post by Grant_Williamson on 2017-09-11
OMG. I'm in "Try Ubuntu" mode from the USB. Can't paste a screenshot now:

 	 		[h=2]vBulletin Message[/h] 		 			 				Your submission could not be processed because a security token was missing.

 If this occurred unexpectedly, please [inform the administrator]("https://ubuntuforums.org/sendmessage.php")  and describe the action you performed before you received this error.  If possible, please include the error page URL plus the date and time  the error occured. 

 Tip : Please shorten long posts by using [https://paste.ubuntu.com/](https://paste.ubuntu.com/) for terminal and log output and link to it in your posts.
 			
 			Ubuntu Forums

---

### Post by Grant_Williamson on 2017-09-11
but gparted says:
Partition | File System | Size | Used | Unused | Flags | 
dev/sda1 | ext4 | 6.84 GiB | 660.86 MiB |
dev/sda2 | ext4 | 924.68 GiB | 777.63 MiB | boot

---

### Post by ian-weisser on 2017-09-11
Yes, it said that before, too.

You partitioned your Ubuntu system so ALL your system files go into /dev/sda1 (6.8GB, full), and ONLY media files go into /dev/sda2 (924.7GB).
One imagines that you had a reason for doing that..and deadflowr is completely correct. The easiest, long-term solution is to fix your partitions so that Ubuntu has enough space to operate.
Implementing that solution may destroy your Ubuntu partition, so be prepared to reinstall.

Pro Tip: ALWAYS assume that messing with your partition table will destroy everything on your disk, so backups are vital. Quite often, changing the partition table does not destroy any data at all. If you are not experienced enough yet to know which changes will destroy and which changes won't, then it's best to be prepared for the worst.

---

### Post by Grant_Williamson on 2017-09-11
> **ian-weisser said:**
> 
One imagines that you had a reason for doing that..


Nope. Sorry. I was flying in the dark using ubuntuforums for research on how to install this new hard drive, on how to do this stuff, that's how it ended up...

> **ian-weisser said:**
> 
The easiest, long-term solution is to fix your partitions so that Ubuntu has enough space to operate.


Thanks. How does one "fix your partitions"? Again. Sorry. I don't know diddleysquat.

---

### Post by ian-weisser on 2017-09-11
One way is: 
1) Back up everything you don't want to lose to some other storage device.
2) Boot from a LiveUSB. (You cannot edit partitions that are mounted)
3) Use GParted on the LiveUSB to move the partition boundary, providing your Ubuntu partition at least 8GB. Heck its a big disk, go for 15GB or so.
4) Try booting back into Ubuntu. If it fails, reinstall a fresh copy from your handy LiveUSB.

---

### Post by Grant_Williamson on 2017-09-12
> **deadflowr said:**
> ```
/dev/sda2       6.7G  6.6G     0 100% /
```
this is the only part that matters, as far as the system is concerned.

You'll need to take some space from the /dev/sda1 partition and add it to the /dev/sda2 partition.

Some basic gparted how to's on moving around partition sizes:
[https://gparted.org/display-doc.php%3Fname%3Dmoving-space-between-partitions](https://gparted.org/display-doc.php%3Fname%3Dmoving-space-between-partitions)

The Ubuntu installation media contains gparted, you can use it in the Try Ubuntu option.

You might want to load the installer Try Ubuntu and take a screen shot of gparted's window and post it in this thread so it would be easier to understand the current partition layout.
And then we should know best way to move things around.

Thanks deadflowr - I figured out how to do the GParted partition size change from the live USB. This seems to have helped! Thanks, I will mark it solved as soon as I get going with normal download stuff. Would I always be restricted to only use the dev/sda2 for downloading new applications? Should I thus get another hard drive, since I could only make that partition 100GB...

---

### Post by ian-weisser on 2017-09-12
100 GB is enormous.
Much more than most people will ever need for their applications and personal data (except huge media files, of course).

Your question about "*[COLOR=#000000]always be restricted to only use the dev/sda2 for downloading new applications[/COLOR]*" has a lot to unpack. The short answer is 'no', but the better answer is that it's the wrong question - downloading and installing applications in Linux is unlike Windows, different skills and constraints apply.

---

