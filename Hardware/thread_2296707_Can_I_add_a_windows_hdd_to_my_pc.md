---
title: "Can I add a windows hdd to my pc?"
date: 2015-09-28
forum: Hardware
---

### Post by thatsnotmyname71 on 2015-09-28
I've recently built a new pc and installed ubuntu on a new hard drive. my old pc ran windows 7 and I took the old hard drive from it. Would it be possible to connect the old hard drive and just select in the BIOS which hard drive I want to use on boot? I prefer using linux for most things the windows hard drive is just for gaming. I read once that you cannot simply transfer hard drives from pc to pc, is this true and if so why?

---

### Post by Bucky Ball on 2015-09-28
Welcome. Fine if it was a Ubuntu OS partition on the drive because most the drivers are right there in the kernel. 

Could be problematic with Windows, particularly if Windows is OEM and was installed on the computer when you bought it. The drivers and settings will probably be specific to that machine and, not only that, if the Windows boot doesn't recognise the hardware as that of the machine it was originally installed to it may not boot at all.

---

### Post by kurt18947 on 2015-09-28
Is the Windows drive from the same machine? I'm no expert (that's an understatement:redface:) but if so, I'd think it'd be possible to have dual boot using separate drives. You may have to muck about in the BIOS - I'm assuming this is not a UEFI BIOS - to set boot order to prevent confusion. My machines will boot the first drive it finds a boot loader installed. I can also press a key during boot to select the boot device without entering the BIOS setup menu. If you have a UEFI BIOS I'm sure there's a selector there as well but I have zero experience with UEFI machines. Things get complicated in my experience when I install Windows on a drive with an existing linux install. Windows boot loader will overwrite GRUB so it's necessary to recreate grub incorporating the Windows boot loader. You don't have this so I'd think you should be fine.

As I understand it, Windows customizes each install, installing drivers and software as appropriate for the hardware found. So if a Windows drive is moved from one machine to a dissimilar machine in terms of hardware, it has to install new drivers and software to match the new machine and there may be conflicts. I've moved Windows disks between similar machines successfully. If I wanted to move a disk from an Intel based machine to an AMD based machine for example, I'd have little confidence in it working and heaven knows how the Windows activation mechanism would react. Linux on the other hand comes with a bunch of drivers present at all times and loads the appropriate ones at boot. So unless there are proprietary drivers in the linux install (video or wifi drivers for example) a linux disk should run on any compatible machine.

---

### Post by Yellow Pasque on 2015-09-28
Put the Windows disk in, boot to Linux, download the necessary Windows drivers, and put them on the Windows disk. At the very least, make sure you have the network driver ready to go, and then you can download any other necessary drivers once you boot Windows and install the network driver.

Of course, if Windows detects a drastic change in hardware (especially mobo), it will ask you to activate again.

---

### Post by yancek on 2015-09-28
>  I read once that you cannot simply transfer hard drives from pc to pc, is this true and if so why? 				

With windows you do not buy the software to use as you want but simply license it for a specific computer.  If you want to install windows on another computer you need to purchase it again.  If your first computer crashed and is unusable you should be able to use it on another computer after you get permission from microsoft.  The hazards of transferring an OEM or even system you installed from the installation medium for windows are explained pretty well above.

---

