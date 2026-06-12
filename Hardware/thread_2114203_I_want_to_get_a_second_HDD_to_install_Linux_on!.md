---
title: "I want to get a second HDD to install Linux on!"
date: 2013-02-09
forum: Hardware
---

### Post by Zeven on 2013-02-09
I have decided to finally put a Linux distribution on my desktop (mostly thanks to a more optimistic look on gaming on Linux) but before investing in a second HDD, I wanted to get clearance from you knowledgeable folk at the Ubuntu forums first. My PC contains the following at the moment:

**CPU:** Intel Core i5 2500K 

**Motherboard:** Gigabyte GA-Z68AP-D3 

**Memory:** 8Gb (2x4Gb) Corsair Vengeance @ 1600Mhz 

**Storage:** 1TB Seagate Barracuda 7200RPM 
[B]
Graphics Card:[/B] Gainward GeForce GTX 570 Golden Sample 

**Power Supply Unit:** Antec TruePower New Modular 650W 

**Case:** Lian-Li PC-K63B First Knight 

**Operating System:** Windows 7 Home Premium 64 bit 

**Monitor:** Yamakasi CatLeap Q270 LED 2560X1440p

The second HDD I intend to get is [this one]("http://www.scan.co.uk/products/2tb-toshiba-dt01aca200-35-hdd-sata-iii-6gb-s-7200rpm-64mb-cache"). I fully intend on keeping Windows 7 around for now especially as I don't find Windows 8 too appealing. Nevertheless, I don't want to play around with partitions and would rather just go all the way by giving Linux its very own HDD. It's a bigger HDD which goes in line with me hoping for Windows 7 to be my last Windows operating system, especially as Linux can do everything I want except sufficient gaming, but even that is changing.

I know that an Intel CPU and a Nvidia GPU will do just fine in Linux. However, what would dual booting from two different HDDs be like? Will I face any issues as opposed to just partitioning the HDD? Is there anything I am missing?

---

### Post by pqwoerituytrueiwoq on 2013-02-09
just add the hdd to the system and make that the primary booting hdd in the bios
then install ubuntu to the new hdd , be sure to but the MBR on the new HDD not the win7 one, that way you can remove the new hdd and have win 7 still boot

you could unplug the win 7 hdd and re connect it after you install ubuntu, but you will need to run [FONT=Courier New]sudo update-grub[/FONT] after you add it to get dual boot

i personally don't trust drive that are over 1tb is capacity

---

### Post by Mark Phelps on 2013-02-09
Big +1 for having the Win7 drive disconnected when installing Ubuntu.  This prevents the all-too-frequent problem of GRUB getting accidentally installed to the Windows drive and hosing up Windows boot in the process.

It's a simple matter when done to reconnect the Win 7 drive, but continue to boot from the Ubuntu drive, open a terminal and enter "sudo update-grub".  When done, you will have a new GRUB config file with an entry for Windows 7.

When you reboot, you should get the GRUB menu with options for both OSs.

---

### Post by cybrsaylr on 2013-02-09
SATA drives have no problems being seen.

I did the same. Have a 2TB HDD for W7 and storage and a second 128GB SSD for Ubuntu. You may want to choose a SSD instead of that HDD you selected since SSDs have greatly dropped in price. Unless you plan to download a lot I would question the need for a 2TB HDD which don't have great track records for reliability. 

My SSD boots up 64 bit 12.04 in ~20seconds and is FAR FASTER than any HDD! 
At first I didn't install or worry about GRUB bootloader because W7 is seldom used. I jut hit F12 if W7 was desired on boot. However after a week normal Ubuntu updates installed GRUB automatically and configured GRUB to my 2 drive setup which really surprised and impressed me. Linix ROCKS! Don't really need Windows at all anymore.

---

### Post by Zeven on 2013-02-09
> **pqwoerituytrueiwoq said:**
> just add the hdd to the system and make that the primary booting hdd in the bios
then install ubuntu to the new hdd , be sure to but the MBR on the new HDD not the win7 one, that way you can remove the new hdd and have win 7 still boot

you could unplug the win 7 hdd and re connect it after you install ubuntu, but you will need to run [FONT=Courier New]sudo update-grub[/FONT] after you add it to get dual boot

i personally don't trust drive that are over 1tb is capacity
Sorry, but what's an MBR? Couldn't I just choose which HDD to boot with or is that different from dual booting?
> **Mark Phelps said:**
> Big +1 for having the Win7 drive disconnected when installing Ubuntu.  This prevents the all-too-frequent problem of GRUB getting accidentally installed to the Windows drive and hosing up Windows boot in the process.

It's a simple matter when done to reconnect the Win 7 drive, but continue to boot from the Ubuntu drive, open a terminal and enter "sudo update-grub".  When done, you will have a new GRUB config file with an entry for Windows 7.

When you reboot, you should get the GRUB menu with options for both OSs.
That sounds good, but I have the same question as above: couldn't I just press Esc and select which HDD to boot from?
> **cybrsaylr said:**
> SATA drives have no problems being seen.

I did the same. Have a 2TB HDD for W7 and storage and a second 128GB SSD for Ubuntu. You may want to choose a SSD instead of that HDD you selected since SSDs have greatly dropped in price. Unless you plan to download a lot I would question the need for a 2TB HDD which don't have great track records for reliability. 

My SSD boots up 64 bit 12.04 in ~20seconds and is FAR FASTER than any HDD! 
At first I didn't install or worry about GRUB bootloader because W7 is seldom used. I jut hit F12 if W7 was desired on boot. However after a week normal Ubuntu updates installed GRUB automatically and configured GRUB to my 2 drive setup which really surprised and impressed me. Linix ROCKS! Don't really need Windows at all anymore.SSDs are still too expensive for the space they give in my opinion. I know that SSDs are superior to HDDs in practically every way except for storage space but that is what matters most to me. I do plan to download a lot after all, but I guess I could switch to a 1TB if reliability is really that bad. Why is worse, though? Aren't there 3TB and 4TB HDDs by now?

---

### Post by cybrsaylr on 2013-02-09
> **Zeven said:**
> .... I guess I could switch to a 1TB if reliability is really that bad. Why is worse, though? Aren't there 3TB and 4TB HDDs by now?

All HDDs 1TB and larger are getting slammed for poor reliability. 
I recently had an OEM 3yr old 1TB Seagate SATA HDD fail.
Replaced it with a 2TB Seagate HDD because of a great 'black friday' price at Newegg but it only came with a 2yr warranty, as opposed to the 5 yr warranty Seagate used to give. 

There is a lot of complaints on a few tech boards on how HDDs > 1TB are failing at higher rates than before. Some think it may be related to SATA drives not being as well made as the old IDE drives which many thing were built to last.....so who really knows.

FWIW I never had an old IDE drive fail but have replaced a couple SATA drives in the last year....

---

### Post by Zeven on 2013-02-09
> **cybrsaylr said:**
> All HDDs 1TB and larger are getting slammed for poor reliability. 
I recently had an OEM 3yr old 1TB Seagate SATA HDD fail.
Replaced it with a 2TB Seagate HDD because of a great 'black friday' price at Newegg but it only came with a 2yr warranty, as opposed to the 5 yr warranty Seagate used to give. 

There is a lot of complaints on a few tech boards on how HDDs > 1TB are failing at higher rates than before. Some think it may be related to SATA drives not being as well made as the old IDE drives which many thing were built to last.....so who really knows.

FWIW I never had an old IDE drive fail but have replaced a couple SATA drives in the last year....

Well, that's discouraging news. SDDs are more reliable, aren't they? There's a Seagate HDD which is 1.20£ more expensive and has one year less warranty so I laughed to myself and ignored it. What about [this one]("http://www.scan.co.uk/products/2tb-wd-red-wd20efrx-sata-6gb-sec-64mb-cache-intellipower-rpm-8ms-ncq-oem-24x7-use")? It advertises with the following:
[QUOTE=Western Digital]Enhanced reliability
With a 35% MTBF improvement over standard desktop drives, the WD Red drive is designed and manufactured to be a more reliable and robust solution.

Longer warranty coverage
The WD Red drive is backed by a 3-year limited warranty for greater peace of mind.[/QUOTE]

Still, IntelliPower seems to imply revolutions per minute far below 7200rpm, plus the price for that HDD is a whole 20£ more.

---

### Post by cybrsaylr on 2013-02-09
In theory SSDs are more reliable than HDDs but some report SSDs burn out in a couple years....so we will have to watch and see. SSDs in Windows PCs burn out quickest because some folks defragg them regularly which is very bad for SSDs. Linux is fortunate here since NO defragging is ever needed. This is a reason I didn't dual boot my 128GB SSD and just put Ubuntu on it....took 8 minutes to install and 9 minutes to update 12.04!

I know little about WD since switching to Seagate when they all came with 5 yr warr. Also don't like that silly 'color coding' WD uses on their drives designating differing 'quality levels', whatever that means. However now all Seagate does is a 2 or 3 yr warr like WD for the most part. WD always used to all come with a 3 yr warr.

---

### Post by pqwoerituytrueiwoq on 2013-02-09
> **Zeven said:**
> Sorry, but what's an MBR? Couldn't I just choose which HDD to boot with or is that different from dual booting?
master boot recored, it tells the system where to look for stuff to boot on the drive
grub will let you choose a OS from a menu regardless of its physical location
letting grub give yuo a chose is more convenient then hitting esc every time
> **Zeven said:**
> That sounds good, but I have the same question as above: couldn't I just press Esc and select which HDD to boot from?
assuming esc is your boot menu, yes; but next time your kernel updates you will have a boot menu in grub

WD blue has a 3 year warranty while there black edition has a 5 year warranty while most seagates have a 2 year warranty
WD owns HGST and Seagate owns Samsung HDDs (i dont think seagate owns there ssds yet)

---

### Post by Zeven on 2013-02-09
> **cybrsaylr said:**
> In theory SSDs are more reliable than HDDs but some report SSDs burn out in a couple years....so we will have to watch and see. SSDs in Windows PCs burn out quickest because some folks defragg them regularly which is very bad for SSDs. Linux is fortunate here since NO defragging is ever needed. This is a reason I didn't dual boot my 128GB SSD and just put Ubuntu on it....took 8 minutes to install and 9 minutes to update 12.04!

I know little about WD since switching to Seagate when they all came with 5 yr warr. Also don't like that silly 'color coding' WD uses on their drives designating differing 'quality levels', whatever that means. However now all Seagate does is a 2 or 3 yr warr like WD for the most part. WD always used to all come with a 3 yr warr.
I cannot remember the last time I performed a defragmention. I just use CCleaner. Does it affect HDDs at all? Glad I'll be switching to Linux if it's so efficient that it does require defragmentation. I also cannot find another HDD in a similar price range that has 24 months worth of warranty so I guess I'll be sticking with that Toshiba HDD.
> **pqwoerituytrueiwoq said:**
> master boot recored, it tells the system where to look for stuff to boot on the drive
grub will let you choose a OS from a menu regardless of its physical location
letting grub give yuo a chose is more convenient then hitting esc every time

assuming esc is your boot menu, yes; but next time your kernel updates you will have a boot menu in grub

WD blue has a 3 year warranty while there black edition has a 5 year warranty while most seagates have a 2 year warranty
WD owns HGST and Seagate owns Samsung HDDs (i dont think seagate owns there ssds yet)Can GRUB be removed? What if I just want to set the Linux HDD as the default HDD and not wait 10 to 30 seconds for it to be selected? Can that be done?

---

### Post by pqwoerituytrueiwoq on 2013-02-09
you can remove grub if you choose but you will not be able to boot ubuntu
google grub customizer for the second part

---

### Post by cybrsaylr on 2013-02-09
> **Zeven said:**
> I cannot remember the last time I performed a defragmention. I just use CCleaner. Does it affect HDDs at all? Glad I'll be switching to Linux if it's so efficient that it does require defragmentation.
By default Windows will defrag your PC once a week if you leave your PC on 24/7, unless your turn that auto feature off.
Some businesses and banks used to defrag their PCs every night!
I use BleachBit instead of CCleaner with Linux. BleachBit serves the same function as CCleaner on Linux with no ill effects to any drives.
And yes Linux require NO defragmentation.
> **Zeven said:**
> Can GRUB be removed? What if I just want to set the Linux HDD as the default HDD and not wait 10 to 30 seconds for it to be selected? Can that be done?
No need to remove GRUB but it can be, shall we say, turned off and on as you desire.

darkod explains how in post #7 of this thread:
[http://ubuntuforums.org/showthread.php?p=12420175#post12420175](http://ubuntuforums.org/showthread.php?p=12420175#post12420175)

---

### Post by oldfred on 2013-02-09
Most motherboards with Intel i-series chips have UEFI/BIOS. I think Gigabyte was one of the last to offer UEFI. Is your motherboard UEFI?

Windows only boots in UEFI mode from gpt drives. Ubuntu will boot in BIOS or UEFI mode from gpt drives. And if drive is over 2TB you have to use gpt. 

Also Ubuntu installs often default to gpt on drives somewhere over 1TB. And to easily dual boot both Windows & Ubuntu have to be UEFI or both BIOS.

Make a small 25GB / (root) partition and separate /home and data partitions. Probably if dual booting with Windows you will want a NTFS shared data partition. Even if Windows (except XP)  is in BIOS mode it will read NTFS data on a gpt drive.

---

### Post by Zeven on 2013-02-10
> **pqwoerituytrueiwoq said:**
> you can remove grub if you choose but you will not be able to boot ubuntu
google grub customizer for the second part
I see. Thank you for the information!
> **cybrsaylr said:**
> By default Windows will defrag your PC once a week if you leave your PC on 24/7, unless your turn that auto feature off.
Some businesses and banks used to defrag their PCs every night!
I use BleachBit instead of CCleaner with Linux. BleachBit serves the same function as CCleaner on Linux with no ill effects to any drives.
And yes Linux require NO defragmentation.

No need to remove GRUB but it can be, shall we say, turned off and on as you desire.

darkod explains how in post #7 of this thread:
[http://ubuntuforums.org/showthread.php?p=12420175#post12420175](http://ubuntuforums.org/showthread.php?p=12420175#post12420175)
Just checked out BleachBit and it says that it's free and open source. I'm switching! I moved from uTorrent to Deluge for the very same reason as well. Thanks! In a way I am finding out more and more how Linux is more user friendly than Windows as I wouldn't expect my parents to maintain a Windows based computer which seemingly requires far more maintenance than Linux does.
> **oldfred said:**
> Most motherboards with Intel i-series chips have UEFI/BIOS. I think Gigabyte was one of the last to offer UEFI. Is your motherboard UEFI?

Windows only boots in UEFI mode from gpt drives. Ubuntu will boot in BIOS or UEFI mode from gpt drives. And if drive is over 2TB you have to use gpt. 

Also Ubuntu installs often default to gpt on drives somewhere over 1TB. And to easily dual boot both Windows & Ubuntu have to be UEFI or both BIOS.

Make a small 25GB / (root) partition and separate /home and data partitions. Probably if dual booting with Windows you will want a NTFS shared data partition. Even if Windows (except XP)  is in BIOS mode it will read NTFS data on a gpt drive.I check [my motherboard's page]("http://uk.gigabyte.com/products/product-page.aspx?pid=3897#ov") and found no trace of UEFI. I also found out what a [GPT drive]("http://en.wikipedia.org/wiki/GUID_Partition_Table") is but really wish I did computer science to understand it fully. Luckily the drive is not over 2TB but the rest goes over my head.

---

### Post by cybrsaylr on 2013-02-10
> **Zeven said:**
> Just checked out BleachBit and it says that it's free and open source. I'm switching! I moved from uTorrent to Deluge for the very same reason as well. Thanks! In a way I am finding out more and more how Linux is more user friendly than Windows as I wouldn't expect my parents to maintain a Windows based computer which seemingly requires far more maintenance than Linux does.
BleachBit 0.9.5 is the latest version and it works great. I run it once a month.
You have to get:
1. BleachBit
2. BleachBit for Administrator, to clean your PC best. Best to get both which may be a bit tricky to find. I recently updated to the latest version but forgot where I got BleachBit for Administrator from. Try Google, as that's how I found it, unless someone can come up with a link or info.

This is the beauty on Linux that it requires far less preventive maintenance than Windows. 

That said with Windows, I've used XP, Vista and Win7 and think they are all solid OSs _as long as you do all the preventive maintenance M$ requires to run well_. Many folks don't bother with this PM which causes all sorts of problems in Windows.

---

### Post by Zeven on 2013-02-13
So I got the new HDD, connected it, disconnected the one with Windows 7 on it, booted up Linux via a USB stick, installed Linux on the new HDD, then restarted, and all I am getting is "Loading Operating System...Read Error...." so I decided to connect the Windows 7 HDD again and there is no second HDD in the Master Boot Record. Not sure what's going on.

---

### Post by oldfred on 2013-02-13
Did you install in UEFI or BIOS mode? And is Windows in same mode. This will show us details.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by Zeven on 2013-02-13
> **oldfred said:**
> Did you install in UEFI or BIOS mode? And is Windows in same mode. This will show us details.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

Thanks for the quick response. [Here's the link!]("http://paste2.org/p/2861258")

---

### Post by Zeven on 2013-02-13
If anyone here can help, I'd be very grateful! [Take a gander.]("http://paste2.org/p/2861258")

---

### Post by oldfred on 2013-02-13
You have a very large drive with just a / (root) and swap. I normally suggest only 25GB for / and create other partitions on drive for /home or data and a shared NTFS data partition if dual booting with Windows.

```
=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 492.135719299 = 528.426704896  boot/grub/grub.cfg                             1
 492.141628265 = 528.433049600  boot/grub/i386-pc/core.img                     1
 492.134727478 = 528.425639936  boot/vmlinuz-3.5.0-17-generic                  1
 492.134727478 = 528.425639936  vmlinuz                                        1
   0.982410431 = 1.054855168    boot/initrd.img-3.5.0-17-generic               3
   0.982410431 = 1.054855168    initrd.img                                     3

```
Note that some files are near start of disk and others at 528GB. Boot-Repair usually suggests a separate /boot. But you can test if the large root is an issue just by using gparted from the live installer you used (& right click swap off) and shrink root to less than 100GB. If that works then we can review alternatives.

---

### Post by oldfred on 2013-02-13
Please do not post the same question in two threads. I did not realize you were the same and answered there. I will move those posts here.

---

### Post by Zeven on 2013-02-13
> **oldfred said:**
> You have a very large drive with just a / (root) and swap. I normally suggest only 25GB for / and create other partitions on drive for /home or data and a shared NTFS data partition if dual booting with Windows.

```
=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 492.135719299 = 528.426704896  boot/grub/grub.cfg                             1
 492.141628265 = 528.433049600  boot/grub/i386-pc/core.img                     1
 492.134727478 = 528.425639936  boot/vmlinuz-3.5.0-17-generic                  1
 492.134727478 = 528.425639936  vmlinuz                                        1
   0.982410431 = 1.054855168    boot/initrd.img-3.5.0-17-generic               3
   0.982410431 = 1.054855168    initrd.img                                     3

```
Note that some files are near start of disk and others at 528GB. Boot-Repair usually suggests a separate /boot. But you can test if the large root is an issue just by using gparted from the live installer you used (& right click swap off) and shrink root to less than 100GB. If that works then we can review alternatives.
This is quite complicated! I would rather just reinstall as I am finding it quite difficult to follow your steps. My apologies; I am quite new to this. So this time I should dedicate some space to / and some to /home, both of which can be ext4, right?
> **oldfred said:**
> Please do not post the same question in two threads. I did not realize you were the same and answered there. I will move those posts here.

Sorry about that. I figured that if I asked in the thread that was suggested, I would get more responses as that thread's purpose is for issues like these.

---

### Post by oldfred on 2013-02-13
If you reinstall, you need to use Something else or manual install to get the options to add more than the default option of / & swap.

You then delete the current Linux partitions. If swap is ok as is you can reuse it.

       You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

    
       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 250 MB efi FAT32 (for UEFI boot or future use for UEFI, you only can have one, so if already existing do not attempt another)
gpt: 1 MB bios_grub no format (for BIOS boot not required for UEFI)
gpt or MBR(msdos)
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

    
How large you make /home or a shared NTFS is up to you. However you do it may be be optimum as even my own best partitioning scheme is obsolete in a year or two.

---

### Post by Zeven on 2013-02-14
> **oldfred said:**
> If you reinstall, you need to use Something else or manual install to get the options to add more than the default option of / & swap.

You then delete the current Linux partitions. If swap is ok as is you can reuse it.

       You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

    
       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 250 MB efi FAT32 (for UEFI boot or future use for UEFI, you only can have one, so if already existing do not attempt another)
gpt: 1 MB bios_grub no format (for BIOS boot not required for UEFI)
gpt or MBR(msdos)
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

    
How large you make /home or a shared NTFS is up to you. However you do it may be be optimum as even my own best partitioning scheme is obsolete in a year or two.

Thank you so much! Disabling the Quick Boot option in the BIOS fixed everything!

Nevertheless, everything worked fine only until I tried to install an Nvidia driver resulting in me getting a black screen at reboot. I have tried pretty much every command I found in my research, but for naught. The black screen remained, what I assume was the Nvidia driver took up 204MB of space and did nothing, and I had to research the following line just to have a user interface again, but that just so happens to run at 800x600 instead of 2560x1440 now. I have been researching for hours now but none of the commands I am using work. One problem leads to another for me.

```
sudo apt-get --purge remove nvidia-current
```

EDIT: Nevermind. I don't know what I did differently after four hours, but it finally installed. Now I just need to get rid of some modtrd file or whatever in etc/init.d to activate X or MDM again. This is far more challenging than I anticipated.

---

### Post by oldfred on 2013-02-14
I have an older nVidia card 9600GT. I have had to use nomodeset on live install and first boot since many versions ago. But with 12.10 I also had to add the linux header first to get nVidia to install from Ubuntu.

       Re: How To Install Nvidia Drivers [v8.1.2.12 by Bogan]. post 1126
[http://ubuntuforums.org/showthread.php?t=1743535&page=113](http://ubuntuforums.org/showthread.php?t=1743535&page=113)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)
# You may need headers - meta package for 12.10 version:
sudo apt-get install linux-headers-generic

    
       # I used nvidia-current-updates & nvidia-settings-updates
            #To see available  versions:
dpkg -l | grep -i nvidia*
apt-cache search nvidia-sett*

---

### Post by Zeven on 2013-02-14
> **oldfred said:**
> I have an older nVidia card 9600GT. I have had to use nomodeset on live install and first boot since many versions ago. But with 12.10 I also had to add the linux header first to get nVidia to install from Ubuntu.

       Re: How To Install Nvidia Drivers [v8.1.2.12 by Bogan]. post 1126
[http://ubuntuforums.org/showthread.php?t=1743535&page=113](http://ubuntuforums.org/showthread.php?t=1743535&page=113)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)
# You may need headers - meta package for 12.10 version:
sudo apt-get install linux-headers-generic

    
       # I used nvidia-current-updates & nvidia-settings-updates
            #To see available  versions:
dpkg -l | grep -i nvidia*
apt-cache search nvidia-sett*

The Nvidia driver has been installed successfully this time! Deleted the nvidia-installer-disable-nouveau.conf file in the modprobe configuration directory which brought nouveau back and thus gave me a graphical user interface instead of a black screen again. Nevertheless, I have lost Cinnamon and no matter what I do, I can't seem to get it back. It's installed, and it's running too apparently, but it won't appear for me.

---

### Post by oldfred on 2013-02-14
Most of the choices for DE are the little icon in upper right of login screen.

---

### Post by Zeven on 2013-02-14
> **oldfred said:**
> Most of the choices for DE are the little icon in upper right of login screen.

That does not work unfortunately.

---

### Post by Zeven on 2013-02-20
oldfred, thanks for all your help! I just wanted to inform you that all the problems presented in this thread were amended after several pleas for help were made on Reddit. There always seems to be an answer with Linux!

[How do I make Cinnamon come back?]("http://www.reddit.com/r/linux4noobs/comments/18jfdr/how_do_i_make_cinnamon_come_back/")

[The Nvidia driver just gives me a black screen...]("http://www.reddit.com/r/linux4noobs/comments/18n1xg/the_nvidia_driver_just_gives_me_a_black_screen/")

---

### Post by AMD64_N_Linux on 2013-02-27
I am about to install Ubuntu 12. I have read and understand the boot portion of the install, I think. : )

My question, is what do I do about all of the partitions on my other 4 SATA HDDs ? There is a mixture of NTFS, and EXT3 data partitions on all of the drives. 

Is there anything I need to do to get ubuntu to see and use those existing data partitions ?

And I already considered and dismissed the idea of getting larger disk, as I am leery of the > 1TB.

I hope that this is still on topic enough to be here, If not I apologize and will move it if an admin or moderator does not beat me to it. 

Thank you.
AMD64_N_Linux

---

