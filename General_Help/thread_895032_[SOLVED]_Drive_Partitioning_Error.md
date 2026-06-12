---
title: "[SOLVED] Drive Partitioning Error?"
date: 2008-08-19
forum: General Help
---

### Post by Yezinki on 2008-08-19
Hi there,

On my Sony Vaio VGC-LS1 machine I formatted , removed OpenSUS & reinstalled Ubuntu Hardy Heron ONLY.

When reinstalling Ubuntu Hardy Heron on reaching step4, I did not do a manual partitioning rather Full Guided one.

Its a 250 GB drive with only 1 OS running.

I am getting errors when I try to install.

LowSky's comments are: 

```
Quote:
Originally Posted by Yezinki View Post
Hi,

Whats wrong with the drive partitions that KDE wont install??

Thanks!
Your / and /home... are both the same size. which is impossible I would fix that. By the way / only need to be about 15GB, you can give the rest to /home
```


How do I fix this??

What should be the partitioning strategy for a SINGLE boot drive using Ubuntu & for a DUAL boot with Vista & Ubuntu??

Hoping to hear from you smart people,

Thanks in advance!

---

### Post by Yezinki on 2008-08-19
How do I correct/fix this??

Thanks!

---

### Post by Yezinki on 2008-08-19
Hello any smart genius man knows how to fix this issue?? 

Kindly help!!

---

### Post by Yezinki on 2008-08-19
None of my genius, smart friends have an answer to this???

---

### Post by oldos2er on 2008-08-19
"I am getting errors when I try to install."

 It would help if you would tell us what the errors are.

---

### Post by jerome1232 on 2008-08-20
You need to be more specific on the errors, also don't bump your own thread for 24 hours.

As far as partitioning scheme it really depends on your usage.

If Ubuntu will be your primary os, then I would partition like this ( you could make them all primary partitions if you want)

```
sda
sda1 primary NTFS 40GB /mnt/windows    
sda5 extended EXT3 15GB /              # maybe 20 if you install ALOT of software
sda6 extended SWAP ~512MB - 2 GB       #if you want to hibernate must be at least as much ram as you actually have
sda7 extended EXT3 all remaining free space /home
```

---

### Post by Yezinki on 2008-08-20
I get errors when I try to install Kubuntu desk top application through the Terminal........it gets downloaded but wont install??

Thats when lowSky saw the screen shot of my drive & gave his comments.

Thanks!!

---

### Post by danwood76 on 2008-08-20
The problem you have is that you have mounted your / through gvfs and so its trying to scan the driver twice from the two seperate locations.
Normally this doesnt happen though gvfs has a lot of problems in hardy.

What you want to do is uncheck the /home/ubuntu line (containing gvfs) from the partition scan and then do the auto partitioning.

---

### Post by Yezinki on 2008-08-20
> **danwood76 said:**
> The problem you have is that you have mounted your / through gvfs and so its trying to scan the driver twice from the two seperate locations.
Normally this doesnt happen though gvfs has a lot of problems in hardy.

What you want to do is uncheck the /home/ubuntu line (containing gvfs) from the partition scan and then do the auto partitioning.

Thanks smart guy........but how do I uncheck the /home/ubuntu line......???

Hoping to hear from you!!

---

### Post by danwood76 on 2008-08-20
On the screenshot you posted there are check boxes next to each line, just click the checkbox next to the second line so as to uncheck it.

Then allow it to do the scan of the filesystem, it won't like scanning the filesystem twice from two seperate locations.
I think thats where your problem lies.

---

### Post by Yezinki on 2008-08-20
Thanks but can't get that kind of file system???

Do I need GParte.........how do I install that?

Thanks again.

---

### Post by Yezinki on 2008-08-20
This is what I get in disk analyzer now.............

---

### Post by danwood76 on 2008-08-20
What do you mean by:
> 
Thanks but can't get that kind of file system???


That screen I am talking about is from the ubuntu installer which uses parted (I think) to do its partitioning.
Which is the same as Gparted.

Its not necessary to do the partitioning before the installer is started because of its internal installer.

When you get to the partitioning stage choose full guided and then make sure to deselect the gvfs partition as I said in my earlier post.

To be honest I'm at a loss as to why GVFS is even sticking its nose in, make sure you dont try to mount the drive you are trying to install to.

---

### Post by Yezinki on 2008-08-20
Hi there, why am I getting this error now?

Thanks!


ubuntu@ubuntu-laptop:~$ sudo apt-get install gparted
[sudo] password for ubuntu: 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
ubuntu@ubuntu-laptop:~$ 
ubuntu@ubuntu-laptop:~$

---

### Post by Yezinki on 2008-08-20
> **jerome1232 said:**
> You need to be more specific on the errors, also don't bump your own thread for 24 hours.

As far as partitioning scheme it really depends on your usage.

If Ubuntu will be your primary os, then I would partition like this ( you could make them all primary partitions if you want)

```
sda
sda1 primary NTFS 40GB /mnt/windows    
sda5 extended EXT3 15GB /              # maybe 20 if you install ALOT of software
sda6 extended SWAP ~512MB - 2 GB       #if you want to hibernate must be at least as much ram as you actually have
sda7 extended EXT3 all remaining free space /home
```


Hi there,

If I don't set Hibernation option on my machines.....than what should be the size of swap file........Physical RAM 2 & 4 GB?

512 MB for 4 GB & 1 GB for 2 GB of RAM??

Thanks!

---

### Post by oldos2er on 2008-08-20
> **Yezinki said:**
> Hi there, why am I getting this error now?

Thanks!


ubuntu@ubuntu-laptop:~$ sudo apt-get install gparted
[sudo] password for ubuntu: 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
ubuntu@ubuntu-laptop:~$ 
ubuntu@ubuntu-laptop:~$

 You can only have one package manager running at one time. If you have Synaptic or Add/Remove open, close them before running that command.

---

### Post by danwood76 on 2008-08-20
You get the lock error when you have synaptic open or the update manager running.
Aptitude, synaptic, etc all use dpkg (Synaptic is really a front end for apt anyway) and only one can be run at a time.

I normaly do a min of 1GB for swap or equal to the RAM amount if hibernate is to be used.
If you plan to do a lot of video editing/encoding or photo work or gaming its worth it to put a bit of extra swap as it can help when you run low but if disk space is a key issue for you then set it to less.

---

### Post by Yezinki on 2008-08-20
Thanks again,



ubuntu@ubuntu-laptop:~$ sudo apt-get install gparted
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  jfsutils ntfsprogs reiser4progs xfsprogs
The following NEW packages will be installed:
  gparted
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/348kB of archives.
After this operation, 2150kB of additional disk space will be used.
Selecting previously deselected package gparted.
(Reading database ... 98012 files and directories currently installed.)
Unpacking gparted (from .../gparted_0.3.5-1ubuntu3_i386.deb) ...
Setting up gparted (0.3.5-1ubuntu3) ...

ubuntu@ubuntu-laptop:~$

---

### Post by jerome1232 on 2008-08-20
> **Yezinki said:**
> Hi there,

If I don't set Hibernation option on my machines.....than what should be the size of swap file........Physical RAM 2 & 4 GB?

512 MB for 4 GB & 1 GB for 2 GB of RAM??

Thanks!

That would work for your standard desktop uses, I have 1 GB of ram and I pretty much never dive into swap.

---

### Post by Yezinki on 2008-08-20
So you feel 512 MB & 1 GB are enough for 4 GB & 2 GB of RAM respectively, if their is no hibernation set?

---

### Post by Yezinki on 2008-08-20
Hi there,

Now how can I correct /fix what lowSky pointed out??

Thanks!!

---

### Post by danwood76 on 2008-08-20
That partition layout is completely fine unless you want a seperate /home partition.

---

### Post by Yezinki on 2008-08-20
Whats right........ if anything in this screen shot of the drive.......1 machine, 1 drive 1 OS??

Thanks!

---

### Post by jerome1232 on 2008-08-20
I don't see anything wrong with that layout either.

---

### Post by danwood76 on 2008-08-20
The other screen shot showed the drive mounted which made no sense.
That layout will work perfectly.

---

### Post by Yezinki on 2008-08-20
Hi there!

1. Isn't /dev/sda1......too large in size for a single OS like Ubuntu...its a primary partition?

2. Shouldn't there be /dev/sda only first?

3. The size of swap is too large for 2 GB of RAM with no hibernation??

4. There is no / & /home??

5. Should swap be after /dev/sda2/?

For a single machine with Ubuntu only

it should be /dev/sd/, /dev/sda1/ /dev/sda2, /dev/sda5/linux swap?

---

### Post by Yezinki on 2008-08-20
> **danwood76 said:**
> That partition layout is completely fine unless you want a seperate /home partition.

Hi there,

Can you tell me how all partitions be seperate & not merged?

Thanks!

---

### Post by jerome1232 on 2008-08-20
sda refers to the whole drive.

sda1 2 3 etc... refer to individual partitions of the drive (sda).

If you want to do a new partition layout reinstalling would be the easiest way, doing a manual partition during the install.

Here's a screenshot of what mine looks like for reference.

---

### Post by Yezinki on 2008-08-20
Wow excellent.........

1. whats jfs......../dev/sda1/......mount.......root....awesome.

2. See you have linux swap next......./dev/sda2/.

3./dev/sda3/......home.........tremendous.

4./dev/sda4/ ......xfs........mntdata..whats that??

Whats jfs & xfs file system??

Incredible!

---

### Post by jerome1232 on 2008-08-20
Normally I don't have that 4th partition it's just / swap /home

But this go around I thought I would try new file systems and a different layout.

jfs is just a different linux file system, (ext3, the tried and true one is the standard) 

xfs is also just a different file system it's supposed to be faster with large files.

There's a whole slew of filesytems (ext2,ext3,reiserfs,xfs,jfs,ufs,ntfs,fat16,fat32), they all have their advantages/disadvantage and there are many wars about said advantages/disadvantages  so I won't get into that but I would stick to ext3 it's considered the most stable.

I store large files (dvdiso's, tar backups, videos) on the /mnt/data partition. 

The way you partition your drive is a whole lot of personal preference imho

---

### Post by Yezinki on 2008-08-20
> **jerome1232 said:**
> Normally I don't have that 4th partition it's just / swap /home

But this go around I thought I would try new file systems and a different layout.

jfs is just a different linux file system, (ext3, the tried and true one is the standard) 

xfs is also just a different file system it's supposed to be faster with large files.

There's a whole slew of filesytems (ext2,ext3,reiserfs,xfs,jfs,ufs,ntfs,fat16,fat32), they all have their advantages/disadvantage and there are many wars about said advantages/disadvantages  so I won't get into that but I would stick to ext3 it's considered the most stable.

I store large files (dvdiso's, tar backups, videos) on the /mnt/data partition. 

The way you partition your drive is a whole lot of personal preference imho


lol....don't make fun of me..........lol again.

I thought reiserfs was fast?

Is your OS primary or is a dual boot??

Thanks!

---

### Post by Yezinki on 2008-08-20
Hey smart man.......Could you have a look at my post Packages.....[http://ubuntuforums.org/showthread.php?t=895090](http://ubuntuforums.org/showthread.php?t=895090)

Why cant i do what i was doing & got dcd at 94%......my luck!

Thanks again........

---

### Post by jerome1232 on 2008-08-20
reiserfs is supposed to excel when handling thousands of small files.
jfs is supposed to be an all around performer
xfs is supposed to be good with large files
ext3 is supposed to be rocksolid

At least that is my very limited and general understanding of these filesystems

google can probably help you out better with learning about various filesystems.

I only run Ubuntu on this computer.

---

