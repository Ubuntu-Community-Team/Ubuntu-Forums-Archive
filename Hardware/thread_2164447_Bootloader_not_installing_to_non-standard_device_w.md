---
title: "Bootloader not installing to non-standard device when installing Ubuntu"
date: 2013-07-31
forum: Hardware
---

### Post by 8WcHQnT on 2013-07-31
Good afternoon, I am not sure if this is the right place to post a question like this but hopefully someone can offer some insights.  I am installing Ubuntu 13.04 on a UEFI machine and everything goes fine until it tries to install the bootloader (Grub).  I believe I know the problem and am hoping someone can shed some light on any options I may have.  The problem is that my device does not show with a standard system device path and therefore I don't think the grub-installer can find it automatically.   The device is a PCI-based SSD and that is part of the reason the name doesn't follow the usual pattern(s) of 'sdX', 'hdX', or maybe 'fdX'.  Either way, changing the path isn't really an option.

The reason I believe this to be the problem is that if I map my device from something like '/dev/xyz' to '/dev/sdX' (and map all the partitions) then grub will start to install without issue.  However, if I don't map it then grub fails to install.  Does anyone know of a way, during install, to tell the bootloader to look for other devices that don't match the usual 'hdX', 'sdX', or 'fdX'?  I have tried creating my own install image where I modified the grub code (which didn't work but I have many theories why) but would prefer not to do this since I would have to distribute that image to customers and there are legal implications invloved with that.  I am afraid that I may have to get the install code changed through Canonical if there is no way to easily modify the installer to look for other devices outside the standard patterns.  

It is probably worth mentioning that if I run grub-install to that device outside the installation environment, then it appears to install without error.  

Hopefully this makes some sense and someone can point me in the right direction.  Thank you.

---

### Post by oldfred on 2013-07-31
When you say it is a PCI SSD what is it?
Some new systems use Intel SRT on SSDs that are part of motherboard or an internal hard drive. But Linux usually sees those as separate devices. But Intel SRT converts them to RAID devices.

With UEFI, you install grub to the efi partition not directly to the MBR of a device anyway. How is efi partition shown?

Are you booting live installer flash or DVD in UEFI mode?

Post this from terminal in live installer.

sudo apt-get install dmraid
sudo parted -l

---

### Post by 8WcHQnT on 2013-08-01
Thank you Oldfred, here are a few answers to your questions.  I also forgot to mention this is for the server version, so that may make a difference.

"When you say it is a PCI SSD what is it?"
-- Assuming I understand your question, the SSD is intended to be the primary hard drive for the system, not a caching device (which is what my limited understanding of SRT would assume it to be).

"With UEFI, you install grub to the efi partition not directly to the MBR of a device anyway. How is efi partition shown?"
-- You are correct.  This is something that I believe should be done automatically when installing on a UEFI-based system (that is, a /boot/uefi/ directory structure is made during installation of the OS on the boot partition).  When installing to a regular hard drive for comparison, this is what I found to be true of the boot partition.  This, of course, assumes that one chooses UEFI mode from the BIOS before running the install DVD, which should answer your next question.

"Are you booting live installer flash or DVD in UEFI mode?"
-- I am booting a DVD in UEFI mode and have not tried live installer (I am not familiar with live installer so I will do a bit of research).

"sudo apt-get install dmraid
sudo parted -l"
-- I will do this now with live installer (assuming it can be used with the server version) and post the output as soon as I get it.

I will admit that I am by no means a Linux guru, or even much more knowledgable than a noobie, so if I am unclear or misguided, feel free to correct me or I will do my best to provide sufficient information.  In fact, here is a bit more info on the process I have to follow since the SSD is not a standard hard drive and not immediately recognized by the system:

1. After powering on the computer, go into the BIOS settings and boot the DVD in UEFI mode.
2. Choose to install the server in regular mode (using expert mode doesn't make any difference, at least none that I have found).
3. Go through the normal setup of the keyboard, timezone, user, etc.
4. The DVD will look for a device to which it can install and will not find any (I have removed all other standard hard drives from the system and my SSD driver is not loaded)
5. Open a console by using Alt+F2
6. Insert a USB and load a driver for my SSD via the 'insmod' command.  
7. Exit the console and instruct the installer to run Detect Disks again
8. My SSD is now found and I can partition it using the standard options (Partition disk and set up LVM option) and begin the installation of the OS.  My device now shows as /dev/bcda, /dev/bcda1, /dev/bcda2 ... (Note that  the 'bcda' is not exactly correct since I am being careful not to use  the exact names for the protection of the company I am working with. The  important thing to note, I believe, is that the name is not the  standard 'sdX' or 'hdX' style).
9. The install will almost complete but the bootloader fails. 
10. I can then choose to continue without bootloader and everything else seems to go fine, but this device is not bootable without the bootloader (obvious statement).

Thanks, again.

---

### Post by 8WcHQnT on 2013-08-01
Here is the output of the 'parted' command.

Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 1      32.8kB  100MB   100MB   fat32                 boot
 2      100MB   1286GB  1285GB  ext4
 3      1286GB  1294GB  8488MB  linux-swap(v1)

---

### Post by oldfred on 2013-08-01
You have a huge / (root) and that is ok, but I prefer to have smaller / partitions, so all of system files are closer together on drive and larger /home or data partitions.

Your explanation of mounting your SSD sounds similar to "fakeRAID"?
       [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Live installer is the Ubuntu desktop as it is a live system and an installer. The server version (or alternative installer with 12.04 but discontinued with newer verisons) are not live systems, but just install versions. Best to have a live version of Linux repairCD/DVD/Flash drive with the same version in case you need to make repairs.

What does BootInfo report show? It may output the mapping you are using. If you do not want that seen do not use the pastebin as that is public and posted automatically, I think?
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

