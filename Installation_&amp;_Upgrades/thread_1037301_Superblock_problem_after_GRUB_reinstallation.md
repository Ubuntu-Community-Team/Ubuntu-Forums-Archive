---
title: "Superblock problem after GRUB reinstallation"
date: 2009-01-11
forum: Installation &amp; Upgrades
---

### Post by melat0nin on 2009-01-11
Hello all

I recently reinstalled XP on its own partition, thereby removed GRUB.  I followed the instructions on the Ubuntu Community wiki to reinstall grub (here - [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows))

That seemed to restore the grub menu, but when I run ubuntu, I get a fsck error about a superblock and am able to log in but without my /home partition being mounted (so all my settings etc are missing of course).

What should I do?  Can I manually run fsck?  I tried that and it warned me it could result in severe damage, so obviously I said 'no'.

Any help much appreciated :)

---

### Post by caljohnsmith on 2009-01-11
How about from your Live CD, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo fdisk -lu
```
And for whichever are your linux partitions do:
```
sudo fsck -yCM /dev/sdaX
```
And replace sdaX with each of the linux partitions. Please post the output of all the above commands, and let me know if you run into any problems. We can work from there if you want.

---

### Post by melat0nin on 2009-01-18
> **caljohnsmith said:**
> How about from your Live CD, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo fdisk -lu
```
And for whichever are your linux partitions do:
```
sudo fsck -yCM /dev/sdaX
```
And replace sdaX with each of the linux partitions. Please post the output of all the above commands, and let me know if you run into any problems. We can work from there if you want.

Thank you, I will try that now and post the results :)

---

### Post by melat0nin on 2009-01-18
> **caljohnsmith said:**
> How about from your Live CD, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo fdisk -lu
```
And for whichever are your linux partitions do:
```
sudo fsck -yCM /dev/sdaX
```
And replace sdaX with each of the linux partitions. Please post the output of all the above commands, and let me know if you run into any problems. We can work from there if you want.

Here is the output of fsck (there appears to be nothing wrong!):

```
ubuntu@ubuntu:~$ sudo fsck -yCM /dev/sda3
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
/home has been mounted 29 times without being checked, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure                                           
Pass 3: Checking directory connectivity                                        
Pass 4: Checking reference counts                                              
Pass 5: Checking group summary information                                     
/home: 117920/12042240 files (1.8% non-contiguous), 16601255/48146805 blocks   
ubuntu@ubuntu:~$ sudo fsck -yCM /dev/sda5
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
/dev/sda5: clean, 141507/915712 files, 1006338/3662812 blocks
ubuntu@ubuntu:~$ sudo fsck -yCM /dev/sda6
fsck 1.41.3 (12-Oct-2008)
fsck: fsck.swap: not found
fsck: Error 2 while executing fsck.swap for /dev/sda6
ubuntu@ubuntu:~$ 

```

I have three linux partitions - system (/dev/sda5), /home (/dev/sda4) and swap (/dev/sda6).  Here is the output of fdisk -lu, if it helps:

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfe96fe96

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   204796619   102398278+   7  HPFS/NTFS
/dev/sda2       204796620   239962904    17583142+   5  Extended
/dev/sda3       239962905   625137344   192587220   83  Linux
/dev/sda5       204796683   234099179    14651248+  83  Linux
/dev/sda6       234099243   239962904     2931831   82  Linux swap / Solaris

```

I don't know if it means anything but the /dev/sda5 check was very quick (like it finished almost instantaneously).  There's not a lot on there (it's just a vanilla Ubuntu system install) but I'd have thought it would take a little longer.

Any thoughts? Your help is much appreciated :)

---

### Post by caljohnsmith on 2009-01-18
It looks like fsck finished OK on both your Linux partitions, so that's a good sign. How about also posting:
```
cat /etc/fstab
```
So when you log in now, does Ubuntu still try to do an fsck on your home partition? Does the home partition still fail to mount? Is sda3 your home partition?

---

### Post by melat0nin on 2009-01-18
> **caljohnsmith said:**
> It looks like fsck finished OK on both your Linux partitions, so that's a good sign. How about also posting:
```
cat /etc/fstab
```
So when you log in now, does Ubuntu still try to do an fsck on your home partition? Does the home partition still fail to mount? Is sda3 your home partition?

I've actually fixed it :)

I looked at the error that came up and it was referring to /dev/sda4, which wasn't listed in the fdisk partition list.

I think when I reinstalled XP, Ubuntu no longer thought of /home as sda4 and instead changed to sda3, so all that I had to do was change the entry in /etc/fstab to read sda3 instead of sda4.

Quite a lot easier than I had expected.. can't believe I was considering a reinstall for what was ***one*** incorrect character!!

Anyway thanks for your help!! :)

---

### Post by caljohnsmith on 2009-01-18
Glad to hear you figured out what the problem was. You might want to consider using UUIDs or partition labels in your fstab instead of device names, because that will prevent exactly the type of problem you experienced, namely having the partition numbers change. In other words, if you do:
```
sudo blkid -c /dev/null
```
That will show the UUIDs for all your partitions, and then in your fstab, in place of /dev/sda3 you could just use "UUID=......" instead. Or partition labels are even better I think, for instance you could do:
```
sudo tune2fs -L "Home" /dev/sda3
```
And then in your fstab, in place of /dev/sda3 you could use "LABEL=Home" instead. That's a lot more meaningful and readable I think, but it is just a suggestion. At least with UUIDs or partition labels you don't have to worry about when your partition numbers change. Anyway, cheers and have fun with your Ubuntu install. :)

---

### Post by melat0nin on 2009-01-19
> **caljohnsmith said:**
> Glad to hear you figured out what the problem was. You might want to consider using UUIDs or partition labels in your fstab instead of device names, because that will prevent exactly the type of problem you experienced, namely having the partition numbers change. In other words, if you do:
```
sudo blkid -c /dev/null
```
That will show the UUIDs for all your partitions, and then in your fstab, in place of /dev/sda3 you could just use "UUID=......" instead. Or partition labels are even better I think, for instance you could do:
```
sudo tune2fs -L "Home" /dev/sda3
```
And then in your fstab, in place of /dev/sda3 you could use "LABEL=Home" instead. That's a lot more meaningful and readable I think, but it is just a suggestion. At least with UUIDs or partition labels you don't have to worry about when your partition numbers change. Anyway, cheers and have fun with your Ubuntu install. :)

Thankyou, I've gone the UUID route and it seems to work well :)

---

