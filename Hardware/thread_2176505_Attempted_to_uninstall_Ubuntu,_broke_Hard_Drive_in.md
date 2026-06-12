---
title: "Attempted to uninstall Ubuntu, broke Hard Drive instead"
date: 2013-09-24
forum: Hardware
---

### Post by nick_2 on 2013-09-24
Hey all

I'm not totally sure if this is the right board to post this on (not even sure if its the right forum). 

A few months ago I installed Ubuntu 12.04 on my Toshiba Satellite P750-15L laptop on its own 200GB partition. Over the course of a few months I broke it enough that it now needed a total reinstall - just by accidentally uninstalling little bits of Ubuntu, and now had enough grip over the OS that I'd reinstall it and hopefully make progress this time from the word Go. 
It is worth noting at this point that Ubuntu was installed alongside Windows 7 Home Premium x64 on the same Hard Drive, which booted through GRUB.

Things started going wrong with the hardware of the laptop fairly early on. Various lights on the case stopped working, like the ones below the 'touch' buttons below the screen, the "Satellite" word on the bottom left of the keyboard, and the light on the trackpad that told you if it was locked or not. They just stay off. Still not really a problem, nothing comprimised the system itself and everything worked fine as far as using the laptop was concerned.

When I uninstalled Ubuntu yesterday, I followed a guide on the correct steps to follow. I followed them as accurately as I could - he article wasn't that clear on some aspects, and it's probably my fault for not having looked at multiple ones beforehand. Time wasn't really something I had on my side at that point. I went through the Disk Management section on Windows and deleted the partitions I guessed were Ubuntu - none of them were notated except the Windows one, so I had to do my best to guess which was the recovery partition, which were Ubuntu partitions, etc. Either way, eventually I was done. I shut down, threw the Windows disk into the drive, got to the Command Prompt on the recovery section, but was only able to run the "bootrec /fixmbr" command. "bootrec /fixboot" refused to work, and the error message was some excuse about the drive being in use. I meh'd and continued on, skipping that instruction. I got back into Windows, reallocated the space on the unallocated partitions to the primary Windows partition, and that should have been that.

The laptop rebooted fine and would load into Windows, but the first sign things were going wrong was the lack of the Toshiba splash screen. Instead of turning on, showing my the big red "TOSHIBA" word with buttons for getting into the setup and BIOS, it just went straight into Windows. There was no way I could access BIOS settings or change the boot order.

Later, I was given an error message on Windows (which was running extremely slowly) that said "Windows detected a hard disk problem" and threatened me with losing all my data if the hard drive failed before the error message next appeared. Basically it was telling me my hard drive had failed in some aspect. My immediate thought was that something had gone wrong with the partition cleansing, and something important was now missing. So I schedule a Disk Check because Windows was then telling me that "jusched.exe" wasn't working either.

I rebooted the machine and it skipped the disk check altogether and just went straight into Windows, then gave me options for Safe Mode boots. I told it to load up in Safe Mode with the intention of reaching command prompt and attempting to "bootrec /fixboot" (suspecting that was the root of the problem) and it is now stuck loading core drivers. The last line reads "Loaded: \Windows\system32\drivers\CLASSPNP.SYS". 

So... I'm not sure if my laptop is about to seppuku on me, or if it was my fault and I screwed up the Ubuntu removal, or if God just hates me right now. Any advice? 

Thanks in advance, I'd really really appreciate any help you can give.

---

### Post by oldfred on 2013-09-24
Do you have a Windows repairCD or flash drive? Or can you make one from another Windows machine at work or school? Must be either 32 bit or 64bit to match yours but can be any version.

Best to only use Windows disk tools to shrink Windows NTFS partitions and use Linux tools like gparted to add or delete partitions as it knows Linux partitions.

Was this a BIOS based or UEFI based install? Either has specific requirements for additional partitions that should not be messed with.

       Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

### Post by nick_2 on 2013-09-24
Hi oldfred, thanks for the fast reply.

I do not have a Windows Repair CD, although my Desktop is a Win7 64bit Home Prem. machine, so I can probably make one on that. I do however have a Windows 7 installation CD, but I don't have the option to boot from the CD at all. It just jumps straight into the installation of Windows on the Hard Disk. 

I read on another site that using gparted would have made my life much easier. We are beyond that stage at this point, unfortunately. 

No idea on the difference between BIOS and UEFI. The Windows installation on the laptop is stock, and the Linux installation was done with a USB boot thingy. Beyond that I won't be able to recall much, unless you ask something specific. I have a terrible memory :(

I will attempt to make a repair CD now.

---

### Post by oldfred on 2013-09-24
You cannot do a lot of Windows repairs from Linux. You can install a Windows like boot loader to the MBR to boot Windows and that is about all for the newer versions. Often chkdsk or other repairs are needed and those need a Windows repair. Sometimes f8 may get you into a repair console but always better to have a repair CD or flash drive.

---

