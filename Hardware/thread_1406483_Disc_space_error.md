---
title: "Disc space error"
date: 2010-02-14
forum: Hardware
---

### Post by Earl-Grey on 2010-02-14
I keep getting the error message that I only have 100 MB free of Hard Drive space and I have about 20GB on my internal hard drive and 100GB via USB. 

Is it possible that my configuration isn't set up properly and is they a way that I can set my default drive to my external one with 100GB free?

After using Unbuntu for a few minutes or hours the system randomly logs out and switches off. I think this is because of this error and by watching youtube or something my supposed 100MB of free space has been used up.

Any help would be great.

---

### Post by chewearn on 2010-02-14
Can you post output of:
```
df -h
```

This command will show the disk space usage.  Please enclose the output in [noparse]```
 
```[/noparse] tag when posting.

---

### Post by Earl-Grey on 2010-02-14
Thank you for offering to help me.

In more detail the error I get states;-
[U][B]
Low Disk Space[/B][/U]
This computer has only 60.2MB disk space remaining.

You can free up disk space by removing unused programs or files, o by moving files to an external disk.

&#9633; Don't show any warnings again

Examine or Ignore

When I typed that code I get this information;-

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0            2.7G  2.5G   73M  98% /
udev                  438M  296K  438M   1% /dev
none                  438M  596K  437M   1% /dev/shm
none                  438M   92K  438M   1% /var/run
none                  438M     0  438M   0% /var/lock
none                  438M     0  438M   0% /lib/init/rw
/dev/sda1              75G   49G   27G  66% /host
/dev/sdb1             299G  200G   99G  68% /media/476C-B627

```

---

### Post by chewearn on 2010-02-14
The root is mounted to /dev/loop0.  Did you install Ubuntu by Wubi?

Anyway, in the short term, you might recover some space by cleaning some cruft:
```
sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get clean
```

---

### Post by Earl-Grey on 2010-02-14
> **chewearn said:**
> The root is mounted to /dev/loop0.  Did you install Ubuntu by Wubi?

Anyway, in the short term, you might recover some space by cleaning some cruft:
```
sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get clean
```

Yes, I had to install linux via Wubi it was the only way I could. My built in disk drive doesn't work and my USB DVD/CD drive can't boot from start up.

As you can tell I don't have the best of computers and am also having trouble with connecting to the internet with Ubuntu.

Is there a way of getting Ubuntu to save its files to my larger USB drive?

Thank you for your help so far ^-^

---

### Post by chewearn on 2010-02-14
Preamble: as far as I know, there is no simple way to get around your problem.  Some work at command line would be required.

[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?)

Please read the page above for options on what you could do.  For instance, increase size of virtual disk, move the virtual disk to dedicated partition, etc.

---

### Post by SecretCode on 2010-02-14
Do you have a lot of customisation already done on this installation? I am tempted to suggest reinstalling but this time specifying at least 10GB for the wubi partition. Otherwise the link posted shows how to use lvpm to expand it.

6GB is the bare minimum - in my opinion - for an Ubuntu installation, even if you are going to store all your data files elsewhere.

---

### Post by Earl-Grey on 2010-02-14
> **SecretCode said:**
> Do you have a lot of customisation already done on this installation? I am tempted to suggest reinstalling but this time specifying at least 10GB for the wubi partition. Otherwise the link posted shows how to use lvpm to expand it.

6GB is the bare minimum - in my opinion - for an Ubuntu installation, even if you are going to store all your data files elsewhere.

I don't really have a lot of work and files in Ubuntu yet. I have been switching between XP and Ubuntu when I can't get the interent to work.

You are right, when I installed Ubuntu through XP I chose the smallest size (maybe 3GB).

On my internal HDD I have about 20 GB and would really want to install Ubuntu on my USB drive with 100 GB plus. Is there any way of getting my bios to read my USB drive or is it one of thoses things where some computers can detect USB drives and others can't.

Anyway thank you both for the help. I think I will re-install Ubuntu later on today.

---

### Post by chewearn on 2010-02-14
> **Earl-Grey said:**
> On my internal HDD I have about 20 GB and would really want to install Ubuntu on my USB drive with 100 GB plus. Is there any way of getting my bios to read my USB drive or is it one of thoses things where some computers can detect USB drives and others can't.

Technically, it's possible to install Ubuntu on external USB drive without BIOS support.  You would need to put the bootloader (Grub and/or /boot directory) in the internal harddisk.

However, practically, this might not be what you want, because the set-up is not straightforward.

---

### Post by Earl-Grey on 2010-02-14
> **chewearn said:**
> Technically, it's possible to install Ubuntu on external USB drive without BIOS support.  You would need to put the bootloader (Grub and/or /boot directory) in the internal harddisk.

However, practically, this might not be what you want, because the set-up is not straightforward.

As I am not that cleaver ;) I think I will stick with using my internal drive for now.

Thank you again for the advice :popcorn:

---

### Post by Earl-Grey on 2010-02-15
> **chewearn said:**
> Preamble: as far as I know, there is no simple way to get around your problem.  Some work at command line would be required.

[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?)

Please read the page above for options on what you could do.  For instance, increase size of virtual disk, move the virtual disk to dedicated partition, etc.


Just wanted to say, I tried that partition program and it's really good. I managed to free up an extra 10GB on my hard drive. 
 
I'm still not sure why I am getting the `You only have 100MB left of drive space` error message. On the drive I installed Ubuntu, I have about 30GB of space but for some reason Unbuntu thinks I only have 100MB or less.
 
 I'm not that good with computers so don't laugh at me if this doesn't make sense. Instead of Ubuntu using the 30GB of free space on my internal drive, does Ubuntu look for undesignated space on the hard drive that hasn't been accounted for yet?

---

### Post by chewearn on 2010-02-16
> **Earl-Grey said:**
> I'm still not sure why I am getting the `You only have 100MB left of drive space` error message. On the drive I installed Ubuntu, I have about 30GB of space but for some reason Unbuntu thinks I only have 100MB or less.
 
 I'm not that good with computers so don't laugh at me if this doesn't make sense. Instead of Ubuntu using the 30GB of free space on my internal drive, does Ubuntu look for undesignated space on the hard drive that hasn't been accounted for yet?

To answer your question, why Ubuntu says it has 100MB remaining, I re-quote your earlier post on "df -h" output.

> **Earl-Grey said:**
> 
```
Filesystem            Size  Used Avail Use% Mounted on
**/dev/loop0            2.7G  2.5G   73M  98% /**
udev                  438M  296K  438M   1% /dev
none                  438M  596K  437M   1% /dev/shm
none                  438M   92K  438M   1% /var/run
none                  438M     0  438M   0% /var/lock
none                  438M     0  438M   0% /lib/init/rw
**/dev/sda1              75G   49G   27G  66% /host**
/dev/sdb1             299G  200G   99G  68% /media/476C-B627

```

So, here is what happened.

1. Look at the line before the last, "/dev/sda1              75G   49G   27G  66% /host". This is your Windows partition.  You probably see the 30GB free space here.

2. By installing using Wubi, you have created a hidden file in this partition (i.e. in Windows, you would see one large hidden file).

3. In Ubuntu, this hidden file is "translated" to a virtual filesystem, and mounted as the root.  This is the first line "/dev/loop0            2.7G  2.5G   73M  98% /"

4. Notice, you have 2.7GB on this virtual filesystem.  2.5GB is used, 73MB is free.

5. Therefore, Ubuntu is allocated only 2.7GB and has 73MB free.  The 30GB free on Windows side is not available for Ubuntu system use as it is.

---

### Post by Earl-Grey on 2010-02-16
> **chewearn said:**
> To answer your question, why Ubuntu says it has 100MB remaining, I re-quote your earlier post on "df -h" output.



So, here is what happened.

1. Look at the line before the last, "/dev/sda1              75G   49G   27G  66% /host". This is your Windows partition.  You probably see the 30GB free space here.

2. By installing using Wubi, you have created a hidden file in this partition (i.e. in Windows, you would see one large hidden file).

3. In Ubuntu, this hidden file is "translated" to a virtual filesystem, and mounted as the root.  This is the first line "/dev/loop0            2.7G  2.5G   73M  98% /"

4. Notice, you have 2.7GB on this virtual filesystem.  2.5GB is used, 73MB is free.

5. Therefore, Ubuntu is allocated only 2.7GB and has 73MB free.  The 30GB free on Windows side is not available for Ubuntu system use as it is.

Ahh, the penny has finally dropped :D Thanks for making it easy for me to understand. So in Windows my Ubuntu installation is seen as a large file but in Ubuntu it is seen as a virtual system.

When installing it I didn't realise this. I thought the installation size was the size of Ubuntu and the larger the size the more files the installation will include and that you could save files to your hard drive like XP.

So, when I next install Ubuntu it is like you are installing a new partition and you have to allocate the appropriate space. :KS

Thanks again

---

