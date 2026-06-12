---
title: "How to get full space out of my hard drive?"
date: 2008-02-13
forum: Hardware &amp; Laptops
---

### Post by murmel on 2008-02-13
I got a new raid 0 system with two 500GB discs and it works great!
But the problem is that I don't get 998 GB as parted tells me but only 915 GB when doing df -h.
I've made it into an ext3 fs with a block-size of 4096.
```
[21:47:18] murmel:~$ sudo parted /dev/sdb print

Disk /dev/sdb: 998GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  998GB  998GB  primary  ext3

Information: Don't forget to update /etc/fstab, if necessary.

[21:49:22] murmel:~$
```
```
[21:50:46] murmel:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
[...]
/dev/sdb1             915G  212M  869G   1% /home
[...]
[21:50:48] murmel:~$
```

Is there any way of getting my lost space back ? =)
Thanks!

- Simon

---

### Post by Jussi Kukkonen on 2008-02-13
*df --si*

That should make your disks bigger :)

---

### Post by murmel on 2008-02-13
Yeah, but then they're calculating it with 1000 mb/gb and not 1024 mb/gb.
Is this that really right?
```
[22:21:25] murmel:~$ df --si
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda1              2.0G   219M   1.7G  12% /
tmpfs                  531M      0   531M   0% /lib/init/rw
udev                    11M    87k    11M   1% /dev
tmpfs                  531M      0   531M   0% /dev/shm
/dev/sda2              988M    32M   906M   4% /boot
/dev/sda8              2.0G    37M   1.9G   2% /tmp
/dev/sda5              9.9G   1.7G   7.7G  18% /usr
/dev/sda6              6.0G   542M   5.1G  10% /var
/dev/sdb1              983G   222M   933G   1% /home
/dev/sda9               47G   240M    44G   1% /root
[22:23:36] murmel:~$
```

---

### Post by Jussi Kukkonen on 2008-02-13
1000s is what disk manufacturers write on the boxes (and what parted shows)

---

### Post by murmel on 2008-02-13
But that means that 15 GB is gone? Do you know where it's hiding? Maybe reserved for something or ... dunno...

---

### Post by of_darkness on 2008-02-16
> **murmel said:**
> But that means that 15 GB is gone? Do you know where it's hiding? Maybe reserved for something or ... dunno...
 [http://en.wikipedia.org/wiki/Gigabyte]("http://en.wikipedia.org/wiki/Gigabyte")  > "As of 2007, most consumer hard drives are defined by their gigabyte-range capacities. The true capacity is usually some number above or below the class designation. Although most manufacturers of hard disks and Flash disks define 1 gigabyte as 1,000,000,000 bytes, the computer operating systems used by most users usually calculate a gigabyte by dividing the bytes (whether it is disk capacity, file size, or system RAM) by 1,073,741,824. This distinction is a cause of confusion, as a hard disk with a manufacturer rated capacity of 400 gigabytes may have its capacity reported by the operating system as only 372 GB, depending on the type of report."  i think that is what the problem is..

---

### Post by habtool on 2008-02-16
Maybe this?

[http://martin.ankerl.com/2008/01/12/get-more-space-out-of-your-ext3-partition/](http://martin.ankerl.com/2008/01/12/get-more-space-out-of-your-ext3-partition/)

I have just discovered that ext3 defaults to reserving 5% of its partition exclusively for root, as a precaution measure that your system does not get FUBAR when you use it for your root partition. I have a 230GB external USB disk that I use for all my big storage requirements, downloaded stuff, backups etc. Due to this reservation I had 11.5GB of unusable disk space, thankfully this is easy to fix:

tune2fs -m 0 /dev/sdf1

Replace sdf1 with your partition name. You don't even have to unmount your disk. Voilá, 11.5 GB more space for free :-) Here is the output of df -h as proof:
Before:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sdf1             230G  193G   26G  89% /media/disk

After:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sdf1             230G  193G   38G  84% /media/disk

---

### Post by murmel on 2008-02-17
Ah, nice!

```
[16:36:44] murmel:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             1.9G  209M  1.6G  12% /
tmpfs                 506M     0  506M   0% /lib/init/rw
udev                   10M   84K   10M   1% /dev
tmpfs                 506M     0  506M   0% /dev/shm
/dev/sda2             942M   31M  864M   4% /boot
/dev/sdb1             915G   46G  823G   6% /home
/dev/sda8             1.9G   35M  1.8G   2% /tmp
/dev/sda5             9.2G  1.6G  7.2G  19% /usr
/dev/sda6             5.5G  275M  5.0G   6% /var
/dev/sda9              44G  229M   41G   1% /root

[16:36:47] murmel:~$ sudo tune2fs -m 0 /dev/sdb1
tune2fs 1.40-WIP (14-Nov-2006)
Setting reserved blocks percentage to 0% (0 blocks)

[16:37:22] murmel:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             1.9G  209M  1.6G  12% /
tmpfs                 506M     0  506M   0% /lib/init/rw
udev                   10M   84K   10M   1% /dev
tmpfs                 506M     0  506M   0% /dev/shm
/dev/sda2             942M   31M  864M   4% /boot
/dev/sdb1             915G   46G  870G   5% /home
/dev/sda8             1.9G   35M  1.8G   2% /tmp
/dev/sda5             9.2G  1.6G  7.2G  19% /usr
/dev/sda6             5.5G  275M  5.0G   6% /var
/dev/sda9              44G  229M   41G   1% /root
```

But still, the size of the drive is 915 G and not 998GB as parted says.

---

### Post by jespdj on 2008-02-18
> **murmel said:**
> But still, the size of the drive is 915 G and not 998GB as parted says.

There's a difference between [gigabytes and gibibytes](http://en.wikipedia.org/wiki/Gigabyte), as someone above already mentioned. Harddisk manufacturers advertise with sizes in gigabytes (multiples of 1000), while a program like 'df' calculates sizes as gibibytes (multiples of 1024). Parted probably calculates in gigabytes.

One terabyte is 10^12 (1,000,000,000,000) bytes, which is something different than one tebibyte (2^40 = 1,099,511,627,776 bytes).

Note that 1 TB = 1,000 GB = 931 GiB. Don't confuse tera/tebi and giga/gibi.

---

### Post by murmel on 2008-02-19
bah, that's so irritating

---

