---
title: "Installing Ubuntu over exsisiting Windows 7 Partition"
date: 2009-01-14
forum: Installation &amp; Upgrades
---

### Post by xprod1gy9x on 2009-01-14
Hello.  I plan to install Ubuntu over my exsisting windows 7 partition.  The problem is, I need help installing it.  I would like to dual boot but I have 3 partitions on my Hard Drive.  How would I install the latest version of Ubuntu over the Windows 7 partition without replacing my C:, and D: drives?

---

### Post by xprod1gy9x on 2009-01-14
Is anyone there?

---

### Post by Gwasanaethau on 2009-01-14
Hi there.

What is the current layout of your hard drive? Is Windows 7 installed on either of your C: or D: drives?

If you have the Ubuntu Live CD, you can paste the following command into your terminal and it will give an overview of your hard disc:
```
sudo fdisk -l /dev/sda
```
NB: If you're using a hard disc that is connected via IDE (rather than SATA) and you're using Ubuntu Version 8.04, you need to use this command instead:
```
sudo fdisk -l /dev/hda
```

---

### Post by xprod1gy9x on 2009-01-14
I have three drives on 1 HDD.  C:(Windows Vista) D:(Recovery from Dell) and W:(Windows 7.

---

### Post by xprod1gy9x on 2009-01-14
> **Gwasanaethau said:**
> Hi there.

What is the current layout of your hard drive? Is Windows 7 installed on either of your C: or D: drives?

If you have the Ubuntu Live CD, you can paste the following command into your terminal and it will give an overview of your hard disc:
```
sudo fdisk -l /dev/sda
```
NB: If you're using a hard disc that is connected via IDE (rather than SATA) and you're using Ubuntu Version 8.04, you need to use this command instead:
```
sudo fdisk -l /dev/hda
```


I'm currently using Windows Vista I want to rewrite Windows 7(16 GB) partition with Ubuntu.  I'm considering taking up 20 GB for the Windows 7 partition.

---

### Post by kranny on 2009-01-14
Get the latest version of ubuntu from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Burn it over a CD(R preferable) with a 4-x speed..

Pop it into your Drive and boot into the live cd and at the partition setup format the third partition (Windows 7) and format it to ext3 and mount it as / 

Make a swap space of 1.5 times your ram..

That should do your job

---

### Post by xprod1gy9x on 2009-01-14
> **kranny said:**
> Get the latest version of ubuntu from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Burn it over a CD(R preferable) with a 4-x speed..

Pop it into your Drive and boot into the live cd and at the partition setup format the third partition (Windows 7) and format it to ext3 and mount it as / 

Make a swap space of 1.5 times your ram..

That should do your job

Thanks a bunch!:)

---

### Post by kranny on 2009-01-14
Why did the mods remove the thanks button:P:P

---

### Post by Gwasanaethau on 2009-01-14
I see, that seems simple enough. The first thing I recommend you do is backup any valuable data on the C: and D: drives. Although you won't be writing to them, there is a very minute possibility that if something goes wrong with partitioning, you might get some data loss. If you've already done that or are willing to take the risk, read on&#8230;

I'll assume you already have the Ubuntu CD ready to go. You can proceed with installing. When you get to the part where it asks for partitioning, select 'Manual' and click next. You will then be presented with a list of partitions and their sizes and filesystems. You want to select the one with the Windows 7 installation (double and triple check this - you can't go back if you make a mistake!) and click 'Delete Partition'. Once this is completed, need to add two partitions - one for your Ubuntu installation, and a small one for the swap partition. The swap partition acts a bit like an extension for your RAM - something like the page file in Windows. People debate how much space you should devote to this partition - anywhere between the same size as your RAM and twice the amount of your RAM should be fine.

As you create these new partitions, you should select 'ext3' as the file system for your Ubuntu partition, and the mount point should be / . For the swap, the file system should be 'swap'.

If you want to add your Windows partitions to be accessible through Ubuntu, click on their partitions and click 'Edit Partition', then select the filesystem as 'NTFS' or 'FAT32' (depending on what format they are already) and the mount point as whatever you wish. For ease of reference, I'd mark them as '/media/windows-c' and '/media/windows-d' respectively. **DO NOT CLICK ON THE FORMAT BUTTON HERE, OR YOU WILL LOSE DATA ON THOSE PARTITIONS!!!**

Once you're happy with your layout, you can proceed with the rest of the installation. Make sure you review all your choices BEFORE clicking on the 'Install' button at the end of the wizard.

I hope this is what you're looking for. Remember, back up your data before you try it just in case something happens during the installation process!

---

