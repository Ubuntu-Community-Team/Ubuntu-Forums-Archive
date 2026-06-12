---
title: "Tripple Booting with Windows 7, XP and Ubuntu"
date: 2009-08-20
forum: Installation &amp; Upgrades
---

### Post by Famico on 2009-08-20
I'd like to preface this by saying I have learned a lot by reading through some of the other topics here, but haven't found something that exactly relates to what I am doing. Also, I'd like to say that I think of myself as having a decent understanding of computers, but not too extensively an understanding of Linux. Anyway...

My goal is to tripple boot Windows 7, Windows XP, and Ubuntu 9.04. If it makes any difference (I don't think it should) I am running an Acer Aspire One, model ZG5. Now, The Aspire One came preloaded with Windows XP. I made a new partition on the drive by splitting the XP partition in GParted, and I installed Windows Seven onto that. At this point, using Windows Seven's boot menu I can switch back and forth between XP and 7 at will.

Here is where I am stuck. 

I have the layout of my partitions as:

Partition          |  File System  |  Label           |  Size
/dev/sda1       |  fat32           |   PQSERVICE | 4.88GiB (Guessing something from Acer)
/dev/sda2       |  ntfs             | ACER            | 89.98GiB (My Windows XP Partition)
/dev/sda4       |  extended     |                     | 13.69GiB
 -- /dev/hda6  | ext3             |                     |  11.72GiB (Want to use for Ubuntu)
 -- /dev/sda5  |  linux-swap   |                     |  1.95GiB
/dev/sda3       | ntfs              | win7             |  46.51GiB (My Windows 7 Partition)

Here is a picture to aid,
[http://kimag.es/share/57942105.png](http://kimag.es/share/57942105.png)

So now I'm wondering how to go about installing Ubuntu. I am okay with keeping the Windows 7 boot loader and having GRUB installed to go between Ubuntu and the Windows 7 boot loader where I can choose between 7 and XP (which I hear is pretty common) or having GRUB give me the option to select any of the three (which I hear is harder to pull off).

I go into the installation, but on the preparing diskspace screen, the installer doesn't recognize the drives correctly. It thinks sda1 is Windows NT/2000/XP, sda2 is Windows Vista (Maybe Vista dumped the loader here? I don't know), and it just identifies the rest of the drives by sda[insert number here], even the actual vista installation.
Here is a picture to show you what I mean,
[http://kimag.es/share/21698934.png](http://kimag.es/share/21698934.png)

So besides that nonsense, in the Ubuntu installation there is the option for "install them side by side choosing between them each startup" and when I click forward to that I get a little popup that states "Before you can select a new partition size, any previous changes have to be written to disk. You cannot undo this operation". So I didn't want to do something I couldn't undo without knowing exactly what I was doing and possibly writing something to a strange partition.

I could also do the third option of Specifying the partitions manually, but I don't get any info about installing GRUB, so I don't want to install Ubuntu to my ext3 partition and then be unable to boot it, or perhaps the system will only want to boot Ubuntu and nothing else.


Now I'm looking for guidence, do I go install them side by side and write the changes, or do I go manually specify the partitions. And if I go with the latter, where and at what point does GRUB come in to the picture?

Thank you for reading.

---

### Post by Mark Phelps on 2009-08-20
It appears that you want to do the following:
1) Install Ubuntu to sda4
2) Install GRUB to sda4
3) Continue to use the MS Windows loader to choose OS's, including Ubuntu

If that's right, I would do the following:
1) Download and burn the GParted LiveCD from distrowatch.com
2) Boot from the GParted LiveCD and use it to create an Ext3 partition and Linux-swap partition inside sda4
3) Reboot using the Ubuntu CD
4) Choose Manual Partitioning during the install.  Do NOT choose side-by-side. 
5) Install Ubuntu to the partitions you selected
6) Install GRUB to sda4, NOT to the MBR of the disk

When done, you will NOT be able to boot into Ubuntu because the MS Windows menu doesn't know about Ubuntu.  To fix that, grab EasyBCD from the NeoSmart Forums, install it, and use it to add an entry to the MS Windows menu for Ubuntu.

If you need detailed help on the latter, check with the NeoSmart forums.  They have How-to's that cover this.

---

### Post by TheHH on 2010-02-11
Hope I'm not hijacking this treat, please tell me if I am.

I have a similar issue, I also want to triple boot Ubuntu, XP and Windows 7, but I already had Ubuntu and XP running on separate HDDs, Ubuntu was installed first, then I installed XP on a separate HDD (with the Ubuntu HDD disconnected), now I did the same for Windows 7, I disconnected all other HDDs (Ubuntu, XP and Data)and installed windows 7 on a separate HDD.

When I connected everything back(Ubuntu HDD, XP, Data HDDs and Windows 7 HDD, Windows 7 does not appear on grub boot menu and now Windows 7 does not boot up by it self.

Is there a way to simply add Windows 7 to Grub so I can have all 3 OS's on grub menu?
Can grub search HDDs to look for OSs to add to the menu?

Funny thing is the XP entry on grub appeared by it self, I've never edited grub to add XP on the booting menu, I was booting directly to XP by going into the BIOS and selecting the XP HDD as my booting drive instead of Ubuntu HDD, somehow XP was added to the grub booting menu.

Thanks in advance!

---

### Post by kansasnoob on 2010-02-11
> **TheHH said:**
> Hope I'm not hijacking this treat, please tell me if I am.

I have a similar issue, I also want to triple boot Ubuntu, XP and Windows 7, but I already had Ubuntu and XP running on separate HDDs, Ubuntu was installed first, then I installed XP on a separate HDD (with the Ubuntu HDD disconnected), now I did the same for Windows 7, I disconnected all other HDDs (Ubuntu, XP and Data)and installed windows 7 on a separate HDD.

When I connected everything back(Ubuntu HDD, XP, Data HDDs and Windows 7 HDD, Windows 7 does not appear on grub boot menu and now Windows 7 does not boot up by it self.

Is there a way to simply add Windows 7 to Grub so I can have all 3 OS's on grub menu?
Can grub search HDDs to look for OSs to add to the menu?

Funny thing is the XP entry on grub appeared by it self, I've never edited grub to add XP on the booting menu, I was booting directly to XP by going into the BIOS and selecting the XP HDD as my booting drive instead of Ubuntu HDD, somehow XP was added to the grub booting menu.

Thanks in advance!

The problem is that you're jumpimng into a very old thread! So people will look at info that has nothing to do with your installation.

Start a new thread!

---

### Post by TheHH on 2010-02-11
I'll do, Thanks!

---

