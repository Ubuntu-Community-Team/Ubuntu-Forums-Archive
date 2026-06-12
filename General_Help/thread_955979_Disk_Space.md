---
title: "Disk Space"
date: 2008-10-22
forum: General Help
---

### Post by Wx Guesser on 2008-10-22
I just installed Ubuntu on a 10GB hard drive and I only have 3.2GB of free space left on the drive. Ubuntu is the only OS on this drive and shouldn't take up that much space. WinXP only took 2GB when it was on it and that includes Office 2000.

On install I had Ubuntu format and partition the drive so nothing else is on it. It made 2 partitions one for the kernel I guess and the rest for everything else. It just seems that an OS that installed from a CD shouldn't need almost 7GB of space.

What should I do to solve this or did I make a mistake on the install? 


Thanks,

Jim W

---

### Post by camoanimal on 2008-10-22
No, that is about average for a Ubuntu install.  It uses atleast 1 gig for swap, but I am using about 2.3  gigs.  And then the barebones OS is almost 3 gigs, and on top of that you have about 1.5-2 gigs of software plus drivers.  I took a loss of about 6.9 gigs when I installed Ubuntu on my HP laptop.

---

### Post by jerome1232 on 2008-10-22
7G sounds like alot to me actually, This isn't even a fresh install and not counting my 18G home folder (which is all added stuff not part of the default installation, there's only text files in there to begin with)

I suppose if you gave 3GB to swap space it makes sense.

My system is only using 6GB and I've installed mplayer,ia32libs,ubuntu-restricted-extras, Nvidia driver, and I have doom 3, and ETQW in my /opt directory. If you take out the stuff in my /opt I'm down to 4GB and that's still more than your fresh install should be.

As far as comparing to XP Ubuntu does come with ALOT more out of the box functionality than XP does.
```

0	/proc
2.3G	/opt
16K	/lost+found
14M	/etc
245M	/lib
7.3M	/bin
4.0K	/mnt
805M	/var
8.1M	/sbin
18G	/home
4.0K	/srv
2.2G	/usr
8.0K	/media
88K	/root
3.3M	/dev
72K	/tmp
0	/sys
26M	/boot
4.4M	/lib32
24G	/
```

---

### Post by anaconda on 2008-10-22
Are you sure you dont have more free space?

If your installation created a /root partition AND a /home parttition, it is possible that both partitions have free space, and the 3,2GB is the free space in your /home partition..

Also How much RAM-memory do you have?
If I remember correctly the default /swap partition size is twice your ram, but if you have atleast 512MB of RAM then you will need only 512-1024MB swap partition.. NO sense in wasting more than that from your small hard drive.  I would recommend a 512MB swap partition.

And when you have so small disk it would be more efficient to have only ONE partition.. no sense in dividing it to separate /root and /home partitions  

That is my humble opinion..

---

### Post by dcstar on 2008-10-23
> **Wx Guesser said:**
> 
........
On install I had Ubuntu format and partition the drive so nothing else is on it. It made 2 partitions one for the kernel I guess and the rest for everything else. It just seems that an OS that installed from a CD shouldn't need almost 7GB of space.

What should I do to solve this or did I make a mistake on the install? 


Firstly, the install process downloads all available updates from the Internet so there can be considerable disk space used because the default is to keep all of these downloaded packages on the root filesystem - you can delete them via Synaptic.

Secondly, the EXT3 filesystem takes a fixed percentage of overhead for the journaling aspect of the filesystem.

Thirdly, Ubuntu is just not an OS, it is a complete usable system that contains many, many packages that a Windows CD will not provide, so there is no basis for comparison.

---

### Post by Wx Guesser on 2008-10-23
OK, I got into Synaptic to see what I could get rid of and the only thing that stood out was a dialer program under the communications header. I don't have a modem installed so it was useless.

How do I locate the older kernel files so I can delete them as well. I'm too new at Linux to just boldly delete things. It took me 2 days to get a decent Linux install as it is. I tried Fedora 9 and that was a disaster. Once I did get it installed, I only had about 1 gig left on the drive. Downloaded Ubuntu and that was a bit smoother but still had its hiccups. There were some Grub problems since the machine is dual boot. I got those ironed out but I would like to recover some disc space.

Thanks,

Jim W

---

### Post by yldouright on 2008-10-26
I was hoping someone here could guide me through an 7.10 install on a pair of small IDE drives (ie: 400MB and 1.6GB). I seem to recall reading that a Debian install only required around 50MB for the "/" partition and 600MB for the /usr. Here was my plan:
1. put the /(root) on a 160MB primary partition at the end of the 400MB drive and use the remainder of this drive for swap space.
2. put the /home on the 1.6GB extended partition.
Is this doable? If not, what has changed from Debian 3.0 (Woody) to increase the /(root) partition requirements? Can I use cfdisk to partition my disk and then manually install to the desired partitions?

---

### Post by yldouright on 2008-11-05
Just to update. I figured out how to configure my installation the way I want it with GParted on Feisty. The trick is to right-click on the /dev and name the partition before you mount it. Using this method, I was able to boot from and old 400MB hard drive. My complete install with swap takes under 3GB. I went with Feisty because I don't need all the wireless stuff.

---

