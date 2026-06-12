---
title: "[SOLVED] Ubuntu 8.04 not detecting partition"
date: 2008-12-21
forum: Installation &amp; Upgrades
---

### Post by trendyabinash on 2008-12-21
Sir I was using Intrepid but I didn't like it, as It does not support my bluetooth device but 8.04 does. So I uninstalled my intrepid and I had read that ubuntu can also be loaded within windows so I did that just to see what is the difference, but I didn't enjoy that also.

So I uninstalled ubuntu 8.04 from add remove and now I want to install it along with my XP, but it is not detecting the partiton table, it was detecting before. It is showing me the whole hard disk as "sda", but not like before as sda1,sda 2 and all. I don't want to loose my valuable data by recreating all the partitons. What should I do? I love ubuntu and now I am without one:( Please help, I am feeling as if a part of me is lost.

PLEASE HELP ME

---

### Post by albinootje on 2008-12-21
> **trendyabinash said:**
> So I uninstalled ubuntu 8.04 from add remove and now I want to install it along with my XP, but it is not detecting the partiton table, it was detecting before. It is showing me the whole hard disk as "sda", but not like before as sda1,sda 2 and all. I don't want to loose my valuable data but recreating all the partitons. What should I do? I love ubuntu and now I am without one:( Please help, I am feeling as if a part of me is lost.

PLEASE HELP ME

If you can, first make a backup of your important data, to some external disk if possible.
And is you XP still booting properly ?

---

### Post by Pumalite on 2008-12-21
Post:
sudo fdisk -lu

---

### Post by trendyabinash on 2008-12-21
yes my xp is booting properly, it is working perfectly fine.

I don't have an external hard drive, thats the problem.

---

### Post by trendyabinash on 2008-12-21
> **Pumalite said:**
> Post:
sudo fdisk -lu
Sir can you please tell me in detail, where do I have to put this?

In the live session ??

---

### Post by albinootje on 2008-12-21
> **trendyabinash said:**
> Sir can you please tell me in detail, where do I have to put this?

In the live session ??

Open a terminal -> Applications -> Accessories -> Terminal
And enter the command there.

---

### Post by trendyabinash on 2008-12-21
I have done it, I am able to see my partitions but the installer is not detecting them
here is output of "sudo fdisk -lu"
```
omitting empty partition (5)

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x236e236d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    62913941    31456939+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2        62926605   312560639   124817017+   5  Extended
Partition 2 does not end on cylinder boundary.
/dev/sda3       104962095   110817125     2927515+  82  Linux swap / Solaris
Partition 3 does not end on cylinder boundary.
/dev/sda5       110817189   146799197    17991004+   7  HPFS/NTFS
/dev/sda6       146799261   230684453    41942596+   7  HPFS/NTFS
/dev/sda7       230684517   312558119    40936801+   7  HPFS/NTFS

```

---

### Post by Pumalite on 2008-12-21
You seem to have a Partition Table problen. Fix it with TestDisk:
[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)
[http://www.sysresccd.org/Howto](http://www.sysresccd.org/Howto)
[http://www.sysresccd.org/Quick-start-guide_EN](http://www.sysresccd.org/Quick-start-guide_EN)

---

### Post by trendyabinash on 2008-12-21
testdisk is used to recover deleted partition
but I want my installer to detect my partition table.

Is it possible through it, if it is then please sir explain me.

---

### Post by Pumalite on 2008-12-21
TestDisk can be used to fix a broken Partition Table too. Read the documentation.

---

### Post by trendyabinash on 2008-12-21
I hope using test disk will not affect my data and windows installation

---

### Post by trendyabinash on 2008-12-21
> **Pumalite said:**
> TestDisk can be used to fix a broken Partition Table too. Read the documentation.
Isn't there a simple way? I am really afraid to loose my data, I can not afford such a loss.

I used testdisk and it is beyond my reach to understand it. Or the fear of loosing all the data is stopping me to take any action.

---

### Post by albinootje on 2008-12-21
> **trendyabinash said:**
> Isn't there a simple way? I am really afraid to loose my data, I can not afford such a loss.

I used testdisk and it is beyond my reach to understand it. Or the fear of loosing all the data is stopping me to take any action.

You don't have a friend or relative with an external usb-disk who can help you out making a backup ? Or burn to DVD ?
Making regular backups is very important anyway.

---

### Post by Pumalite on 2008-12-21
You can save your data, reformat your hard drive. Then reinstall everything; Windows first; Ubuntu last.

---

### Post by trendyabinash on 2008-12-21
is there any other way please help.

Sir, testdisk can rebuild partition table but by doing so I will loose all my data, which I don't want to.

---

### Post by trendyabinash on 2008-12-21
> **Pumalite said:**
> You can save your data, reformat your hard drive. Then reinstall everything; Windows first; Ubuntu last.
Sir I used the testdisk, sorry it took me a little time to understand it but I managed some how.

Now I am up and running with my Ubuntu 8.04, but it is not able to load nvidia drivers, If I will not be able to load it I will post on other forum.

THANK YOU A LOT.

---

