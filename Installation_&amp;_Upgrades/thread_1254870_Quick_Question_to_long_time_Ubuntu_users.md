---
title: "Quick Question to long time Ubuntu users"
date: 2009-08-31
forum: Installation &amp; Upgrades
---

### Post by pizza-is-good on 2009-08-31
Hi, I have been using Ubuntu for a while now, and since then have upgraded a few times. Since my last upgrade was little buggy, I though that when karmic comes out, I'm just gonna do a fresh install.
 
What I plan to do, and here is where I need someone to confirm that what I'll be doing is OK, is to go in with a liveCD or usb, format my ubuntu partition, and then install karmic on that. That's how I guess an OS in uninstalled, but please tell me if I'm wrong.
What I can't figure out is if my grub will take care of itself, or if I'll need to do anything to it.
I am currently dual booting Vista and Jaunty.
 
One other thing, should I format my partition as Ext4, or should I just stik with Ext3?

---

### Post by Bachstelze on 2009-08-31
You don't even need to do anything with your partitions beforehand. Just run the Karmic installer, and you can format your partitions in it. GRUB should automatically recognize your XP installation, just like it did the first time you installed.

As for ext3 vs. ext4, I can't really say anything. I personally stick with ext3, since I don't really see a reason to move to ext4.

---

### Post by presence1960 on 2009-08-31
> **HymnToLife said:**
> .

As for ext3 vs. ext4, I can't really say anything. I personally stick with ext3, since I don't really see a reason to move to ext4.

Good advice. I use ext4 for / only. My data/storage partitions are ext3. Ext 4 is snappier compared to ext 3. So I get that benefit on my OS partition.

---

### Post by anujpathania on 2009-08-31
If you use Windows dual boot, why not use Wubi?

Installing and uninstalling ubuntu is a piece of cake in it.

---

### Post by presence1960 on 2009-08-31
> **anujpathania said:**
> If you use Windows dual boot, why not use Wubi?

Installing and uninstalling ubuntu is a piece of cake in it.

wubi is not meant to be a permanent solution. it is a temporary "test drive" to check out ubuntu for those unwilling to commit to partitioning their hard disk until they are sure they like Ubuntu. Since wubi is installed inside the windows filesystem it is subject to performance degradation due to windows filesystem fragmentation.

see [here]("https://help.ubuntu.com/community/Wubi")

---

### Post by presence1960 on 2009-08-31
Wubi (Windows-based Ubuntu Installer) is an official Windows-based free software installer for Ubuntu.

Wubi was born as an independent project and as such versions 7.04 and 7.10 were unofficial releases.[2] Since 8.04 the code has been merged within Ubuntu and since 8.04 alpha 5, Wubi can also be found in the Ubuntu Live CD.[1]

The goal of the project is to assist a Windows user unacquainted with Linux in trying Ubuntu without risking any loss of information due to disk formatting or partitioning.[2] Wubi can also uninstall Ubuntu from within Windows.

It is not a virtual machine, but rather, it creates a stand-alone installation within a loopmounted device, also known as a disk image, like Topologilinux does. It is not a Linux distribution of its own, but rather an installer for Ubuntu.[1]

Users interested in directly installing to a dedicated partition, like a standard Ubuntu install does, without needing a CD should use UNetbootin instead.[3]

While Wubi does not install Ubuntu directly to its own partition (which the developers consider a feature) this can also be accomplished by using LVPM, the Loopmounted Virtual Partition Manager, to transfer the Wubi-generated Ubuntu installation to a dedicated real partition, including a bootable USB keydrive.[1] [COLOR="Red"]The advantage of this setup is that users can test the operating system and install the drivers before they install it to a dedicated partition (and avoid booting and functioning risks).[/COLOR]

Wubi adds an entry to the Windows boot menu which allows the user to run Linux. Ubuntu is installed within a file in the Windows file system (c:\ubuntu\disks\root.disk), as opposed to being installed within its own partition. This file is seen by Linux as a real hard disk. [1] Wubi also creates a swap file in the Windows file system (c:\ubuntu\disks\swap.disk), in addition to the memory of the host machine. This file is seen by Ubuntu as additional RAM.[1]

above taken from: [http://en.wikipedia.org/wiki/Wubi_(installer](http://en.wikipedia.org/wiki/Wubi_(installer))

wubi is just a test drive, not a permanent solution, although I realize some are using it permanently.

---

### Post by SoftwareExplorer on 2009-08-31
About Ext4 vs Ext3: I use ext4 for things I can replace, like an ubuntu install, and make my /home folder and all my other data folders on Ext3 because more programs support it (I'm mostly talking about backup/recovery programs.) That way booting is supposedly faster, and I don't have to worry about data loss.

---

### Post by pizza-is-good on 2009-09-07
Thanks everybody for your comments and help.
 
> **SoftwareExplorer said:**
> About Ext4 vs Ext3: I use ext4 for things I can replace, like an ubuntu install, and make my /home folder and all my other data folders on Ext3 because more programs support it (I'm mostly talking about backup/recovery programs.) That way booting is supposedly faster, and I don't have to worry about data loss.
 
SoftwareExplorer thanks for bringing the thread back to the original topic. And thanks for the answer.
That sounds like a good idea, so I'l probably do that.
 
Now question:
 
I now how to make another ext3 partition, buut how do I asign /home to it?

---

### Post by presence1960 on 2009-09-07
> **pizza-is-good said:**
> Thanks everybody for your comments and help.
 

 
SoftwareExplorer thanks for bringing the thread back to the original topic. And thanks for the answer.
That sounds like a good idea, so I'l probably do that.
 
Now question:
 
I now how to make another ext3 partition, buut how do I asign /home to it?
not to be smart but i said that 6 days ago in post # 3.:popcorn:

---

### Post by SoftwareExplorer on 2009-09-07
> **pizza-is-good said:**
> Thanks everybody for your comments and help.
 

 
SoftwareExplorer thanks for bringing the thread back to the original topic. And thanks for the answer.
That sounds like a good idea, so I'l probably do that.
 
Now question:
 
I now how to make another ext3 partition, buut how do I asign /home to it?
First, a message of warning:These instructions assume you are going to use an empty (at the time of install) partition for /home.
When you run the installer off the live CD, you just want to choose manual partitioning  when it asks. Then make a partition that is 'used as' ext 4, and set it to be mounted on / (it lists common places to mount stuff in the drop down box), (you'll probably want to format this partition). Then make your data that is used as ext3 and and mounted on /home.
As far as grub goes, it should work fine, only really cares where / or /boot are, and /home is fstab's area to take care of.

---

### Post by pizza-is-good on 2009-09-16
> **presence1960 said:**
> not to be smart but i said that 6 days ago in post # 3.:popcorn:

Sorry. I guess I should pay attention to what I read next time. :lolflag:

> **SoftwareExplorer said:**
> First, a message of warning:These instructions assume you are going to use an empty (at the time of install) partition for /home.
When you run the installer off the live CD, you just want to choose manual partitioning  when it asks. Then make a partition that is 'used as' ext 4, and set it to be mounted on / (it lists common places to mount stuff in the drop down box), (you'll probably want to format this partition). Then make your data that is used as ext3 and and mounted on /home.
As far as grub goes, it should work fine, only really cares where / or /boot are, and /home is fstab's area to take care of.

Gotcha! Thanks

---

### Post by fanglinyong on 2009-09-16
i thought the ext3 should be more stable!!I use ext3 for my whole disk!

---

