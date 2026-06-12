---
title: "Copying Data Hangs Again"
date: 2016-12-24
forum: Hardware
---

### Post by ThePowerpuffGirls on 2016-12-24
I thought I had fixed this issue by connecting the drive directly to SATA, but it started again. It froze while copying data over before, I was doing updates, and everything wasn't going forward, the updates and the copying.
Now, I'm copying 93.5GB and it's stuck at 616.8MB, and nothing is moving. I think the drive is dying or something. It'll move a little, and then stop for at least a few minutes, it is at 1.2GB now.

Also, with each progress, the ETA gets longer, from an 1h 30m to 2h 33m to 6 hours.

UPdate:

```

alexa@Alexas-PC:~$ sudo fsck -r /dev/sdb1
[sudo] password for alexa: 
Sorry, try again.
[sudo] password for alexa: 
fsck from util-linux 2.27.1
e2fsck 1.42.13 (17-May-2015)
/dev/sdb1 is mounted.
e2fsck: Cannot continue, aborting.




/dev/sdb1: status 8, rss 2888, real 0.002274, user 0.000000, sys 0.000000
alexa@Alexas-PC:~$ sudo umount /dev/sdb1
alexa@Alexas-PC:~$ sudo fsck -r /dev/sdb1
fsck from util-linux 2.27.1
e2fsck 1.42.13 (17-May-2015)
6TBHDD contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Block bitmap differences:  -651732640 -(1118535680--1118674977)
Fix<y>? yes

```

Update 2:
After doing the above command, and restarted the computer, it works without hanging, needless to say, I'm getting rid of the drive ASAP, as I have to do maintaince seemingly almost every time I have to copy data to it. I think it is defective.

Update3:
It hanged again at the last 2 items to go, at 53s to go.
Going through the routine again.
fsck -r, restart and copy the last two files. It seems to be getting worse.

```

alexa@Alexas-PC:~$ sudo umount /dev/sdb1
[sudo] password for alexa: 
alexa@Alexas-PC:~$ sudo fsck -r /dev/sdb1
fsck from util-linux 2.27.1
e2fsck 1.42.13 (17-May-2015)
6TBHDD contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
6TBHDD: 6563/183140352 files (6.1% non-contiguous), 1096945909/1465122048 blocks
/dev/sdb1: status 0, rss 62076, real 32.124406, user 5.912000, sys 0.248000
alexa@Alexas-PC:~$ 

```

---

### Post by ThePowerpuffGirls on 2016-12-27
I've backed up all the data and reformatted it to EXT4 again, this time in the Disks management, despite that it generally crashes for some reason upon formatting. I used gparted before.
As I'm copying the data back, I played a video that has already copied on the drive, and no there doesn't seem to be any freeze, nor is there any interruptions in the file transfer. I assume whatever the problem was, was a faulty format, somehow.

I will wait until all the data is back and give it a couple of days before marking it as solved just to make sure.

- Alexa

---

