---
title: "For the love of god someone help me with my RAID0"
date: 2005-10-25
forum: Hardware &amp; Laptops
---

### Post by groovywombat on 2005-10-25
please someone anyone, i need to be able to mount my existing RAID0 array in breezy. i don't want to boot from it, I just want it to be useable in Ubuntu. The devices show up 
```
Disk /dev/hde: 80.0 GB, 80054059008 bytes
255 heads, 63 sectors/track, 9732 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1               1       19465   156352581    7  HPFS/NTFS

Disk /dev/hdf: 80.0 GB, 80054059008 bytes
16 heads, 63 sectors/track, 155114 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

Disk /dev/hdf doesn't contain a valid partition table

```
Ive tried installing the dmraid software, but I can't seem to ativate /dev/hdf my guess is that it lacks a valid aprtition table, but since it's a striped raid i don't think it would have one.

The RAID device is a Promise MBFastTrak133 Lite which is built into my Gigabyte 7VAXP Ultra Motherboard, the hdds are IDE. I'll be trying to boot of a single unpartitioned IDE drive.

pleasesomeone help me or direct me to another place I can get help.please
please
please.....

---

### Post by Saarg on 2005-10-25
Have you tried this
```
sudo dmraid -ay -v
```

What is the output?
If it says activating RAID then try this
```
ls /dev/mapper/
```

What is the output then?

Hope this helps.

---

### Post by groovywombat on 2005-10-28
thanks for the response it took a me a while becuase i've been without power for the last 3 days.  anyway i have run those commands but all i get is 
```
ERROR: hpt37x: wrong # of devices in RAID set "hpt37x_eccadiicdi" [1/2] on /dev/hde
ERROR: removing inconsistent RAID set "hpt37x_eccadiicdi"
No RAID sets

```

so when i run /dev/mapper/  I only get ```
control  Ubuntu-root  Ubuntu-swap_1
```
so any other ideas?  
thanks again

---

### Post by groovywombat on 2005-11-14
please someone help....

---

### Post by skylark on 2005-11-15
In what config was the raid last working (eg was it working under a different linux install?).

---

### Post by groovywombat on 2005-11-16
It has never worked.  i'm trying to get it working for the first time

---

### Post by skylark on 2005-11-17
Okay  - your best bet is avoid the hardware raid side of things and go straight to software raid (mdadm). Software raid is extremely flexible, has great in-built monitoring and error reporting capacity and is thoroughly tested. Software raid has negligible CPU overhead nowadays.

To get mdadm working you might first need to disable the hardware raid side of things in the BIOS. Then you need to partition both drives and set the partition type to linux-raid autodetect (you can use fdisk /dev/hdf or similar for the "f" drive for example). Then (from memory) do something like:

```
sudo mdadm --create /dev/md0 --chunk=128 --level=0 --raid-devices=2 /dev/hd[ef]1
mkfs.ext3 /dev/md0      # or use xfs, reiserfs etc instead of ext3

```

should get you a raid-array like you want.

If you want to use your array as a data store, you could mount /dev/md0 somewhere eg:
sudo mkdir /mnt/myarray
sudo mount /dev/md0 /mnt/myarray 
(or better setup up /etc/fstab to do this automatically), and then just copy stuff to /mnt/myarray.

If you want to use it as a basis for your entire system then you should be able to install directly to software raid during the Ubuntu install. It is possible to do it post install as well (I do it this way for setting up raid-1, although I use LVM as well).

If you are interesting in setting up LVM on raid this may help you: [http://home.gagme.com/greg/linux/raid-lvm.php](http://home.gagme.com/greg/linux/raid-lvm.php)

Do a search for mdadm raid on google and you might also find some other pointers.
A nice article with an overview of mdadm is at:
[http://www.linuxdevcenter.com/pub/a/linux/2002/12/05/RAID.html](http://www.linuxdevcenter.com/pub/a/linux/2002/12/05/RAID.html)

PS: if you are using raid-0 be aware that if one drive fails you may not be able to recover your data. You might be better off with raid-1 if you value your data or raid-5 if you can add in more hard-drives to the setup.

---

### Post by groovywombat on 2005-11-20
I appreciate the help but I'm trying to keep all my current data on the drive... but i may give up on it entirely when my new hdd comes, becuase then i can just copy all the data over.i just need to figure out the best way to set up the RAID so i can still use it to play games in windows, but still be able to write to the drive without sudo.  
thanks anyway though

---

