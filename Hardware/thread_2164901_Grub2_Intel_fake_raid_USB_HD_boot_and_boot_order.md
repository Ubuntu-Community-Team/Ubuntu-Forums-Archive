---
title: "Grub2 Intel fake raid USB HD boot and boot order"
date: 2013-08-02
forum: Hardware
---

### Post by thomasjj2 on 2013-08-02
I'm not sure if this is the place to post this, but here goes.

I have installed Ubuntu 12.04 onto an external usb WD passport drive.  It is a full install and I use the drive for diagnostic and demonstration purposes since it is a full install.   I actually have few questions that I can't seem to find an answer to in my searches.

1.)  The drive boots fine if you select it as the first hard drive in the bios.  However if you go to a bios one time boot screen and boot from there, you will more times than not be dumped to a grub rescue prompt with a file not found.  Doing an ls and manually selecting the drive will then resume the boot.  My question is this...  Is there a way in grub2 to basically tell it that the boot folder is on the same drive that the bootloader is found.  I know that syslinux can, since a live usb never has any problems.  Normally grub2 only knows drive numbers which are determined by the order that the bios looks for them, which can be problematic if you are booting from a USB on a computer with an unknown setup of internal drives.

2.)  This is the I tried to boot a computer with an Intel fake raid 1 setup.  The computer is running windows xp and it is not encrypted.  The computer boots and runs fine (albeit slowly).  When I went to boot from the usb drive, it dropped me to grub rescue and an ls only showed the 2 internal hard drives.  The usb drive was not listed.  I had changed the bios to look for the usb drive before the raid volume, but grub still couldn't see my external drive.  I then booted fine from the usb live 12.04 disk.  Which brings me to another question...

3.)  When I booted from the live usb I tried to mount the internal volume with dmraid, but got an error message saying "ERROR: dos: partition address past end of RAID device".  My experience is very similar to this thread  [http://ubuntuforums.org/showthread.php?t=1184371](http://ubuntuforums.org/showthread.php?t=1184371).  I have also found other outside threads saying that this isn't a problem with dmraid rc14 (ex: [https://bbs.archlinux.org/viewtopic.php?id=77329](https://bbs.archlinux.org/viewtopic.php?id=77329)).  I find it odd that this hasn't been fixed in all these years.


Sorry about the number of questions and maybe I should have split them up into multiple threads, but I experienced them all at the same time.  Thank you in advance.

---

### Post by oldfred on 2013-08-02
If external drive is sdb and you can boot into it, you just install grub to the MBR of sdb with this:
       #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

    

I do not know RAID, but may be best to see details.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by thomasjj2 on 2013-08-02
> **oldfred said:**
> If external drive is sdb and you can boot into it, you just install grub to the MBR of sdb with this:
       #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub



This is exactly what I have done.  However, you place the eternal drive on a computer with two internal drives and your use the one time boot from the bios and all of a sudden the sdb becomes sdc or if you have switched it in the bios to be first, it is now sda...  this plays havok with the initial hdx setup of root in grub2.  This can be gotten around fairly easily by hitting "e" and editing the commands manually to the proper hdx and a quick update-grub will fix it for that setup for next time...  but with a roaming usb drive next time will be on a different setup.

I believe my specific issue is mainly due to grub not being able to see the usb.

---

### Post by oldfred on 2013-08-02
As long as you use UUID the search for UUID overides the hd0 setting. Also with grub the drive you boot from is always hd0, and then drives in grub are in BIOS order.

I have had similar issues years ago before the search function and did have to manually update the hdX entry. 

I currently boot from sdd, but that sometimes is sde as I skipped a port in my motherboard. If I add a flash drive it becomes sde, but if I reboot with flash still in, flash becomes sdb or sdc (the skipped port in order) and my boot is then from sde but still works.

---

### Post by thomasjj2 on 2013-08-03
Alright, so I am guessing that my issue has more to do with this particular hardware setup.  There are about 15 of these computers that I am trying to work with all with this same setup.  The only difference is that some have raid and some don't.  The ones with the raid don't work at all, the ones without do work with the editing.  I'll try the boot scan of the raid setup next chance I have to go into the facility with the computers.

---

### Post by oldfred on 2013-08-04
Are you keeping the RAID? If not you need to remove RAID meta-data from the drives.

---

