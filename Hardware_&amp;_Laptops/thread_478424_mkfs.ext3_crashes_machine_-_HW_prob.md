---
title: "mkfs.ext3 crashes machine - HW prob?"
date: 2007-06-19
forum: Hardware &amp; Laptops
---

### Post by halfdan.k on 2007-06-19
Hi
this was originally posted under general help ([http://ubuntuforums.org/showthread.php?t=314061](http://ubuntuforums.org/showthread.php?t=314061)), but I'm starting to suspect, that it may actually belong here.

My box is an IBM T40, 40GB HDD, standard issue, running a brand new Feisty install. This is the only problem I've encountered so far, and it mystifies me. During recent install the entire hdd was repartitioned and formatted w/o incident. Currently I am attempting to setup truecrypt following an online tut. 

The issue crops up when having mapped the truecrypt volume to /dev/mapper/truecrypt0 I try to
$mkfs.ext3 /dev/mapper/truecrypt0
and it hangs. 
First I tried with a 10GB volume, which resulted in it hanging during writing the inodes - no mouse, no dropping to terminal, nada. Several reboots meant the hang occured later in the inodes process, but it never finished.

I subsequently tried deleting the original volume and creating a new 4GB one, and once again mkfs.ext3 it. This resulted in mkfs completing inodes writing and journal creation steps, but then hanging in the last step. This is where I am currently stuck. 

I would assume there is no physical flaw on my hdd due to the recent succesful format and install. But still mucking about with the size and such of the volume seems to affect things - so do I have a HW issue, a laptop issue or just gremlins? Having not found any threads previously relating to this except one, I'm pretty clueless. 

Any and all thoughts much appreciated. Thx.

---

### Post by halfdan.k on 2007-06-21
*bump*

---

### Post by neptho on 2007-06-21
You're using TrueCrypt, which is software.

If you were able to partition the hard disk without issues, it's most likely a problem within TrueCrypt.  You can test to see if your loopback device or a module is crashing in dmesg.  Keep in mind that it may just take awhile since it has to run the whole thing through a loopback virtual device.

When formatting, you can see your ongoing read/write stats like so:

```
%vmstat -d 4 | grep sd
```

---

### Post by xorwen on 2007-11-17
I have the same problem. The system stucks just a few seconds after execution
```
sudo mkfs.ext3 /dev/mapper/truecrypt0
```
During this time the amount of allocated memory was highly incerasing (hundereds of MB), but the HDD was still working (for 6 hours without any result)

I have Gutsy Gibbon, external USB HDD and truecrypt-4.3a. With command
```
sudo mkfs.vfat /dev/mapper/truecrypt0
```
everything goes fine.

---

### Post by StevenHarper on 2007-11-25
This is a clipping from a Truecrypt Forum Entry that may help

[http://forums.truecrypt.org/viewtopic.php?t=4205](http://forums.truecrypt.org/viewtopic.php?t=4205)

[I]Just wanted to visit since I may have found cleaner solution for mkfs.ext2 freezing problem than space-eating loopback trick. It seemed to me that caching disk i/o is what freezes the system and thought that what if we would make mkfs.ext2 to sync() while it creates inode tables? Googled for a while and it seems that it is already implemented: [http://www.ussg.iu.edu/hypermail/linux/kernel/0211.3/0386.html](http://www.ussg.iu.edu/hypermail/linux/kernel/0211.3/0386.html)

So before creating filesystem, just set environment variable MKE2FS_SYNC like this:

export MKE2FS_SYNC=10

Then create filesystem normally:

mkfs.ext2 /dev/mapper/truecrypt0

Worked for me with 100GB container. Didn't try without setting MKE2FS_SYNC this time so can't be sure, but havent done anything else to my system than added disks, so this could probably work with everyone. Hope this helps![/I]

---

### Post by d351GuJu on 2007-12-04
> **StevenHarper said:**
> This is a clipping from a Truecrypt Forum Entry that may help

[http://forums.truecrypt.org/viewtopic.php?t=4205](http://forums.truecrypt.org/viewtopic.php?t=4205)

[I]Just wanted to visit since I may have found cleaner solution for mkfs.ext2 freezing problem than space-eating loopback trick. It seemed to me that caching disk i/o is what freezes the system and thought that what if we would make mkfs.ext2 to sync() while it creates inode tables? Googled for a while and it seems that it is already implemented: [http://www.ussg.iu.edu/hypermail/linux/kernel/0211.3/0386.html](http://www.ussg.iu.edu/hypermail/linux/kernel/0211.3/0386.html)

So before creating filesystem, just set environment variable MKE2FS_SYNC like this:

export MKE2FS_SYNC=10

Then create filesystem normally:

mkfs.ext2 /dev/mapper/truecrypt0

Worked for me with 100GB container. Didn't try without setting MKE2FS_SYNC this time so can't be sure, but havent done anything else to my system than added disks, so this could probably work with everyone. Hope this helps![/I]

Thanks for posting the solution, I experienced same problem when I was trying to create ext3 as well as ntfs partition.  The solution you provided works for ext3 partition; however, does not work for NTFS.  So anyone out there who is trying to create NTFS volume and everything freezes , well there really is no solution so far.  Hope this saves someones time and multiple reboots.  :popcorn:

---

### Post by d351GuJu on 2007-12-09
Turns out it doesn't work actually, it was very close to completing the process but it hung up on me and had to do a reset :/

---

### Post by godmode_uk on 2007-12-12
Hi

I have also run into this problem and I have unfortunately not been able to solve it. However vfat formatting does work for me although this is not ideal because of the 2gb file size limit. So I have resorted to using reiserfs

apt-get install reiserfsprogs
mkfs.reiserfs /dev/mapper/truecrypt0

Although its not ext2/3 at is a good filesystem and gives good functionality. Hope this helps a little.

Regards

---

### Post by d351GuJu on 2007-12-12
> **godmode_uk said:**
> Hi

I have also run into this problem and I have unfortunately not been able to solve it. However vfat formatting does work for me although this is not ideal because of the 2gb file size limit. So I have resorted to using reiserfs

apt-get install reiserfsprogs
mkfs.reiserfs /dev/mapper/truecrypt0

Although its not ext2/3 at is a good filesystem and gives good functionality. Hope this helps a little.

Regards

Thanks, that helped!  I now have 145GB of external truecrypt drive which has been converted to Reiserfs filesystem but the only problem I have now is whenever I copy large files, the transfer rate starts out at 10MB/s and just drops to 2MB/s after a minute later.  I am connected to USB2.0, anyone else having similar problems?  I was able to copy large files to it when I didn't truecrypted the entire drive, but now it takes forever to copy files.

---

### Post by godmode_uk on 2007-12-13
Hi glad that helped. I am running a 600GB encrypted reiser system.

Unfortunately you are almost certainly  running into an inherent issue with encryption. It puts overheads on to the cpu to encrypt and decrypt the file system which will result in slower throughput. This is the reason that scp/sftp will give you slower transfer rates than vanilla ftp. Added to the fact you are using usb I suspect that this is the reason and not some fundamental hardware problem.  It's just the way it is if you want security.

Regards

---

### Post by godmode_uk on 2007-12-13
By the way are you absolutely sure that you are connected to a usb2 port and not a usb1 port. Most machines have a usb1 port as well as usb2.....

---

### Post by d351GuJu on 2007-12-13
> **godmode_uk said:**
> By the way are you absolutely sure that you are connected to a usb2 port and not a usb1 port. Most machines have a usb1 port as well as usb2.....

Yes, I assembled the system myself and positive that all ports are USB2.0, actually the throughput I used to achieve when the ext. hdd had no encryption was roughly 22-25MB/s and now that I have encrypted it, it's down to 2.5-5MB/s, this is what makes me assume that it is a software issue.

---

### Post by wieman01 on 2008-03-20
The freeze problem still persists. Some HDs cope fine with 'ext3', some just hang and results in a complete system freeze.

Anybody with a smart idea for a remedy?

---

