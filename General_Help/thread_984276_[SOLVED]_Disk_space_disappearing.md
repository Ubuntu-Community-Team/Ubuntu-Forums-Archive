---
title: "[SOLVED] Disk space disappearing"
date: 2008-11-16
forum: General Help
---

### Post by homer693 on 2008-11-16
Every time I try to free up any disk space it will disappear instantly so i have 0 bytes of free space, what keeps taking up my disk space, its ubuntu 8.10 Intrepid Ibex running from my live usb

---

### Post by cariboo on 2008-11-16
What size is your usb device? There several programs that cache settings and files, including Firefox. If you install any programs the packages are stored in /var/cache/apt/archives. If you upgrade the kernel the old kernel is not automatically removed. If you used the USB boot disk creator program to create your Ubuntu-on-a-stick how much space did you set for persistence?

Jim

---

### Post by homer693 on 2008-11-16
I set 208.0 mb for the persistence file, its a 1 gb usb thumb drive,

---

### Post by homer693 on 2008-11-16
And when I install any programs, I remove their packages after installing to save space, I've emptied my firefox cache, so I don't know why everytime I try to free space up, the space fills up by itself

---

### Post by unutbu on 2008-11-16
Run 
```

df
```

The output might look something like this:
```

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda3            299463656  62122516 234298752  21% /

```
Notice the following odd thing:

The 1K-blocks (299463656) do not equal the Used (62122516) + Available (234298752) space.
(62122516+234298752=296421268).

The unaccounted-for space are reserved blocks. Reserved blocks are reserved for root to use only. If you filesystem fills up completely, then you wouldn't be able to boot because /var/log/messages gets written to during boot, and if you literally had no space, then /var/log/messages could not be written to (among other things that would fail). 

So there are reserved blocks that allow root to write a bit to things like /var/log/messages, even when df says there is no available space.

So if when you run df you see that 100% of the space has been used, it is likely that you are also relying on root's reserved space. When you delete files to reclaim space, root reclaims its reserved space before normal users get to see any improvement. So it might seem as though you deleted stuff and yet regained no space.

If the above does not apply because your "Use%" is not 100%, please post the output
of df before and after you delete something. For example,
```

actor@studio:~% df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda3            299463656  62170032 [COLOR="Red"]234251236[/COLOR]  21% /
varrun                  517084        96    516988   1% /var/run
varlock                 517084         0    517084   0% /var/lock
udev                    517084       100    516984   1% /dev
devshm                  517084         0    517084   0% /dev/shm
lrm                     517084     34696    482388   7% /lib/modules/2.6.22-14-generic/volatile
```
```
actor@studio:~% ls -l /tmp/linux-2.6.25.tar.bz2 
-rw-r--r-- 1 actor actor 48601689 2008-11-16 16:36 /tmp/linux-2.6.25.tar.bz2
actor@studio:~% rm /tmp/linux-2.6.25.tar.bz2 
rm: remove regular file `/tmp/linux-2.6.25.tar.bz2'? y
```
```
actor@studio:~% df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda3            299463656  62122516 [COLOR="Red"]234298752[/COLOR]  21% /
varrun                  517084        96    516988   1% /var/run
varlock                 517084         0    517084   0% /var/lock
udev                    517084       100    516984   1% /dev
devshm                  517084         0    517084   0% /dev/shm
lrm                     517084     34696    482388   7% /lib/modules/2.6.22-14-generic/volatile

```
```

234298752-234251236=47516 1K-blocks regained.
47516*1024=48656384 bytes
48656384-48601689=54695 bytes unaccounted for
```

---

### Post by homer693 on 2008-11-16
Here's the results from df, I couldn't delete anything because there wasn't enough space to make a file to delete:
```

Filesystem           1K-blocks      Used Available Use% Mounted on
tmpfs                   224212      2000    222212   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                   224212      2000    222212   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                   224212         0    224212   0% /lib/init/rw
varrun                  224212       216    223996   1% /var/run
varlock                 224212         0    224212   0% /var/lock
udev                    224212      2740    221472   2% /dev
tmpfs                   224212      1024    223188   1% /dev/shm
rootfs                  206269    195649         0 100% /
/dev/sdb1               978928    928448     50480  95% /cdrom
/dev/loop0              691712    691712         0 100% /rofs
tmpfs                   206269    195649         0 100% /tmp
tmpfs                   224212      2000    222212   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                   224212      2000    222212   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                   224212      2000    222212   1% /lib/modules/2.6.27-7-generic/volatile

```
I see that there is extra space available but only used by root, but what is taking up all my space?, i only have the default ubuntu applications, I tried removing old packages and clearing firefox cache but it still doesnt do anything

---

### Post by pavel123 on 2008-11-26
I have [the same problem]("http://ubuntuforums.org/showthread.php?p=6256389") (without solution yet). It looks like a bug.

---

### Post by pavel123 on 2008-11-27
I created [a bug report]("https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/302703") on launchpad.

---

### Post by pavel123 on 2008-12-03
I've figured-out [the root of the problem]("http://ubuntuforums.org/showthread.php?p=6304135#post6304135").

---

### Post by homer693 on 2008-12-20
I'll just give up on ubuntu for now until I can backup my files and install it to the hard drive.

---

### Post by pavel123 on 2008-12-21
You can try direct installation to a flash drive from [VirtualBox]("http://www.virtualbox.org/") (booted-up from Ubuntu ISO image as CD-ROM, without any HDDs connected to VM). It is an absolutely safe way so you don't have to back up data.

---

### Post by homer693 on 2008-12-27
> **pavel123 said:**
> You can try direct installation to a flash drive from [VirtualBox]("http://www.virtualbox.org/") (booted-up from Ubuntu ISO image as CD-ROM, without any HDDs connected to VM). It is an absolutely safe way so you don't have to back up data.
Doesn't Ubuntu require at least 4gb though? because I only have a 1gb flash drive

---

### Post by pavel123 on 2008-12-29
> Doesn't Ubuntu require at least 4gb though? because I only have a 1gb flash drive

Default Ubuntu installation takes about 2GB of disk space (excluding swap, which is not used with flash drives).

You can consider [installation from Alternate CD]("https://help.ubuntu.com/community/Installation/LowMemorySystems").

However it seems that for such a small drive it's better to stay with compressed usb-creator's installation and simply avoid updates.

---

