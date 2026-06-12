---
title: "Wubi or Partition?"
date: 2009-09-06
forum: Installation &amp; Upgrades
---

### Post by ParkerH19 on 2009-09-06
So I'm trying to decide whether I should just use Wubi or if I should partition the drive. Are there any negatives to either?

---

### Post by ninjapirate89 on 2009-09-06
I'm pretty sure a Wubi install is slightly slower (Not really a noticeable amount). If you already know for sure that you like Ubuntu enough to commit to a dual boot then that is what I would suggest.

---

### Post by aeiouna on 2009-09-06
I think it also depends on how confident you are working with computers. I'm not confident enough, personally, to create a partition (and didn't want to muck up Windows, it's still my main OS), so I went with Wubi and have loved it.

---

### Post by ParkerH19 on 2009-09-06
Thank you both! I'm going to use Wubi tomorrow!

---

### Post by presence1960 on 2009-09-06
Wubi is not meant to be a permanent solution. it is meant to be a test drive for those who are now unwilling to commit to partitioning their disk. See [here]("https://help.ubuntu.com/community/Wubi").
> 
Wubi (Windows-based Ubuntu Installer) is an official Windows-based free software installer for Ubuntu.

Wubi was born as an independent project and as such versions 7.04 and 7.10 were unofficial releases.[2] Since 8.04 the code has been merged within Ubuntu and since 8.04 alpha 5, Wubi can also be found in the Ubuntu Live CD.[1]

The goal of the project is to assist a Windows user unacquainted with Linux in trying Ubuntu without risking any loss of information due to disk formatting or partitioning.[2] Wubi can also uninstall Ubuntu from within Windows.

It is not a virtual machine, but rather, it creates a stand-alone installation within a loopmounted device, also known as a disk image, like Topologilinux does. It is not a Linux distribution of its own, but rather an installer for Ubuntu.[1]

Users interested in directly installing to a dedicated partition, like a standard Ubuntu install does, without needing a CD should use UNetbootin instead.[3]

While Wubi does not install Ubuntu directly to its own partition (which the developers consider a feature) this can also be accomplished by using LVPM, the Loopmounted Virtual Partition Manager, to transfer the Wubi-generated Ubuntu installation to a dedicated real partition, including a bootable USB keydrive.[1] [COLOR="Red"]The advantage of this setup is that users can test the operating system and install the drivers before they install it to a dedicated partition (and avoid booting and functioning risks).[/COLOR]

Above taken from Wubi-wiki @ [http://en.wikipedia.org/wiki/Wubi_(installer](http://en.wikipedia.org/wiki/Wubi_(installer))

---

### Post by MasterNetra on 2009-09-06
**_Wubi_**

**Advantages**: You get to keep windows without having to dual boot, have the MBR messed with, also easy to remove should you not want it. (sense its installed under windows like a program)
**Disavantages**: Somewhat slower, and might fragment quicker over time sense its on a NTFS partition. Also neither can access one another (windows usually can't touch Ubuntu anyway, but in Wubi Ubuntu can't touch Windows, I think)

**_Partition_**

**Advantages**: Runs better, Ubuntu is capable of accessing window's files.
**Disadvantages**: Keeping Windows means dual booting and messing with the partitions, which can be risky. (Risky really if you need to yank memory from window's partition, which is common, or if you move a partition as such setting up dual booting ***may not*** be as straight forward.)

**Advice**: Start off with Wubi, if you want keep Ubuntu and want to use it solely and at its best then install it over windows. However if you need windows for something but still want to use Ubuntu in all its glory, read up on dual booting, then **backup** all information you can't or don't want to lose, then go ahead and set everything up.

---

### Post by presence1960 on 2009-09-06
> **MasterNetra said:**
> **_Wubi_**

**Advantages**: You get to keep windows without having to dual boot, have the MBR messed with, also easy to remove should you not want it. (sense its installed under windows like a program)
**Disavantages**: Somewhat slower, and might fragment quicker over time sense its on a NTFS partition.

**_Partition_**

**Advantages**: Runs better...Theres more but it has slipped my mind at this time.

**Disadvantages**: Keeping Windows means dual booting and messing with the partitions, which can be risky. (Risky really if you need to yank memory from window's partition or if you move a partition.), setting up dual booting is not as straight forward.

Partitioning is not that hard, but nothing is guaranteed. There are plenty of info & how to's in this community alone to have some one up to speed and able to partition their disk no matter what their level of expertise. That's what back ups are for and why we suggest to back up your data prior to installing/partitioning! Everytime you boot your machine and use it you are at risk of data loss/MBR corruption, etc. from a variety of things, usually operator error. Should we not boot our machines to avoid all that?

Putting Ubuntu on a dedicated partition is the way to go. if you aren't sure you want Ubuntu and just want to try it use wubi temporarily.

---

### Post by MasterNetra on 2009-09-06
> **presence1960 said:**
> Partitioning is not that hard, but nothing is guaranteed. There are plenty of info & how to's in this community alone to have some one up to speed and able to partition their disk no matter what their level of expertise. That's what back ups are for and why we suggest to back up your data prior to installing/partitioning! Everytime you boot your machine and use it you are at risk of data loss/MBR corruption, etc. from a variety of things, usually operator error. Should we not boot our machines to avoid all that?

Putting Ubuntu on a dedicated partition is the way to go. if you aren't sure you want Ubuntu and just want to try it use wubi temporarily.

I didn't say it was hard, just that it MIGHT not be straight forward. I'm just laying things out. Though Jaunty and above (and maybe Interpid..I forget) at least does well with that sense the installer can pretty much do the work for ya..unless you want a specific sized partition and windows is hogging all at that moment, but meh.

---

