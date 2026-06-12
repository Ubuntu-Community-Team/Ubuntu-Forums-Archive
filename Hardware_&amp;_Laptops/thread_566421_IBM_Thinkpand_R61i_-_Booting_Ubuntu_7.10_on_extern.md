---
title: "IBM Thinkpand R61i - Booting Ubuntu 7.10 on external HD"
date: 2007-10-03
forum: Hardware &amp; Laptops
---

### Post by minuialwen on 2007-10-03
I have installed Ubuntu 7.10 on a 500G external drive that I've partioned to split the drive between windows file system types and unix reiser.  A few vfats for sharing files and an NTFS basically for backups of the main OS on the laptop.  Then just a few spare unix partions and the install ones.  

Install went fine and I told it to install Grub on HD1 so that it would put it on the MBR of the external drive.  As far as I know that should of stuck it on the next physical drive and ingored if it was external, internal, etc.  That seemed to go fine it gave no errors.

I went into the bios and made sure anything that was USB was top of boot order list.  However shuffled the fake CDROM off the boot list(my external tricks to show a partion as a cdrom it is an Acom drive which is apprently a repackaged Seagate).  

Anyways on boot it doesn't see the MBR on the external(USB drive) and offer me Grub.  It boots directly to Windows.  I installed Grub on the externals MBR so that I'd only be prompted to choose OS when the external drive is connected.  So that windows could run unbothered if the other drive wasn't attached.  aka I was trying to avoid putting Grub on the MBR of HD0.  

I did go into the BIOS and tried to see if turning on always on for USB would make a difference and it made no difference.  I'm assuming the USB driver is loaded early in boot otherwise USB devices wouldn't be offered on my BIOS startup boot order screen.

Anyone have any suggestions as to how to get Ubuntu to work from this laptop?  As I said install process went fine.  I'm trying to figure out why Grub isn't being called when my external is attached so I can log into Ubuntu.

I did ask my hardware and network operating systems teachers if they had any idea what might be up they weren't sure but thought maybe the USB driver isn't being loaded.

Thanks,

Minu

---

