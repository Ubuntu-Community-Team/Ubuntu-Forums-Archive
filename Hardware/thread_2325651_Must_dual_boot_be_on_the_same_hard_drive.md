---
title: "Must dual boot be on the same hard drive?"
date: 2016-05-24
forum: Hardware
---

### Post by makem2 on 2016-05-24
I have one HD in a laptop at the moment and this has Windows 10 and Xubuntu on it as a dual boot system.

I want to use an SSD drive for Linux only as I only use the Windows install if I really have to.

Could I replace the unused CD drive with an SSD hard drive and install a fresh Xubuntu on there, copying the Home folder, and still have a dual boot system across the two drives?

Would it be a better option (as in performance), to replace the current HD with the SSD and put the current HD in the CD bay? I prefer the first option as it does not involve taking the laptop apart.

---

### Post by oldfred on 2016-05-24
Is system UEFI or BIOS.
Grub only boots from ESP - efi system partition on sda.

Do you know if you can directly boot from a drive in CD drive bay?
We have seem some that do and others that only boot from first drive. Some of those were able to install grub to MBR of internal drive and boot, others had to have a full /boot partition on internal drive which then might negate the advantage of an SSD.

Also SSD only supports trim with AHCI. And AHCI is only available if SATA drive. Is CD considered a SATA drive from BIOS?

Most laptops make it pretty easy to swap drives.

---

### Post by makem2 on 2016-05-24
System is UEFI
The laptop does not have a CD installed but has the bay and connections internally.
I can boot from USB and assume therefore I could boot from the CD drive.
I can turn off Fast Boot.
Toshiba Satellite Model: P50-C-12Z

I install windows on a small partition, then install xubuntu on partitions I choose. One of those is / and Home is on another partition as is swap.

---

### Post by oldfred on 2016-05-24
Do not know specifics on your model.

Some other threads, maybe comments will help?
 Can't boot into Ubuntu on a Windows 8 machine (Toshiba P50) Manually copy files cp & mv
[http://ubuntuforums.org/showthread.php?t=2257259](http://ubuntuforums.org/showthread.php?t=2257259)
[URL="http://ubuntuforums.org/showthread.php?t=2261061"]http://ubuntuforums.org/showthread.php?t=2261061
[/URL]
 Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Another users in same thread used Legacy mode and then NIC worked.
Toshiba P50 reset with pin hole on bottom
after tinkering, i found a little pinhole on the bottom of the laptop next to the RAM. used a paperclip to press it and now the BIOS is working again. 
[http://ubuntuforums.org/showthread.php?t=2237148](http://ubuntuforums.org/showthread.php?t=2237148) 

[URL="http://ubuntuforums.org/showthread.php?t=2261061"]
[/URL]

---

### Post by makem2 on 2016-05-24
Nothing there of help thanks.

The machine is dual booting perfectly, no problems whatsoever. I just want the xubuntu on an ssd and the Windows on the fitted HD with as much interference with the laptop as possible.

Am investigating these:

[http://linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)

[http://linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/](http://linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/)

As I already have a working dual boot on the existing HD I assume I can install a fress xubuntu on the SSD which should pick up winblows and the other xubuntu and give me three boot options??

If that works I could delete the existing xubuntu after transferring required data and edit the grub?

Does this sound like a working plan?

Anybody have a dual boot Linux/Linux?

---

### Post by gordintoronto on 2016-05-26
Yes, I dual-boot Linux and Linux. At the moment my desktop has Mint 13 and Xubuntu 15.10 on the hard drive, and Xubuntu installed on a 32 GB flash drive. (True installation, not a liveUSB.)

My laptop has W10 and two versions of Linux; that's where I do most testing.

---

### Post by makem2 on 2016-05-27
Is it simply a matter or sorting out the partitions and grub makes three independent boot entries? Are there any drawbacks?

My grub has and entry 'Ubuntu'. Do you have to edit the grub to identify which OS is which?

---

### Post by oldfred on 2016-05-27
Grub2's os-prober spoils us. It makes it easy to add boot stanza for just about any other install. 
But you get its defaults.

You can edit each install's name in /etc/default/grub, comment out default name & add yours.
 sudo nano -B /etc/default/grub
#GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_DISTRIBUTOR="Xubuntu-12.04-amd64 Precise"
sudo update-grub 

But easier then to to start managing grub yourself. You can manually add one boot stanza to 40_custom that does not need updating with kernel updates in your other installs, and has whatever description you desire.
 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
[https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays)

---

### Post by makem2 on 2016-05-27
Thanks all.

[http://linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/](http://linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/)

I will use that as a guide.

---

