---
title: "Cannot boot Ubuntu anymore - BIOS can't find proper boot settings - no loader found!"
date: 2012-10-06
forum: Hardware
---

### Post by happyslurpies on 2012-10-06
Ubuntu (insert latest version) has worked perfectly fine since I made my USB bootable and placed the .iso on it.
 
I've been using the LiveCD in RAM for weeks, but one day I decided to mess with the devices (to try and partition the drive, which was dumb of me) and I changed the file system in a drop-down-box listing to another similar one with a different address and restarted.
 
The OS won't boot, and BIOS will dump on the screen "Operating system not found" now.
 
It's my fault for messing with stuff I wasn't aware of - but here's where I really need help .... HOW DO I FIX THIS???!!!
 
I've searched around everywhere, and as far as I know there's no questions on this problem.
 
Should I format the volume again, and place the bootloader and .iso back on the drive again after partitioning, or do I do something else?
 
Please help! I've just been learning Ubuntu, the terminal commands, and I Just installed Code::Blocks (I'm a computer programmer), but I can't figure out how to solve this problem!
 
I've done everything on BIOS, but this is obviously something with the drive's boot flags, and/or hexadecimal memory address.
 
PS: I am NOT dual-booting, I only have one bootloader and disc image of Ubuntu on my USB, and one computer system(aside from another in the house I have access to). I have only one working(previously)OS, which is Ubuntu. I need to write stuff for work, and I can't afford to buy any tools/other devices to boot an operating system/ROM device program!

---

### Post by ajgreeny on 2012-10-06
Try **Boot Repair** from the info at [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by happyslurpies on 2012-10-09
I assume you didn't read my full message.
 
My USB has an adjusted boot sector, and BIOS can't find the bootloader(GRUB).
 
The .iso means nothing if BIOS can't even load Ubuntu thru bootsector in the first place.
 
That is, unless you want me to mount the .iso on another OS, but that won't be easy(I don't have access to other computers much).
 
I can't boot the .iso because GRUB can't be found. Please read thoroughly before jumping to inconvenient conclusions so fast.

---

### Post by YannBuntu on 2012-10-09
Just to be sure, do you mean you can't even boot on your Ubuntu liveUSB ?

---

### Post by ajgreeny on 2012-10-09
OK, I think I understand what you are saying.

If I am right, you had grub 2 on the MBR of a USB flash drive which would have made a /boot folder on the drive.  In that /boot folder there was a folder named  grub and another called iso.

By manually editing the grub.cfg file in the grub folder you could simply boot the .iso file of ubuntu.
Am I correct?

If I am you can probably get back to where you were originally by repeating the grub installation to the MBR of the flash drive with ```
sudo grub-install --root-directory=/media/USBFolderName /dev/sdx
```where sdx is your flash drive, and then copying the iso file back again to the /iso folder.

All the info I have given here can be found in more detail at [http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)

If I am still missing your point I apologise, but I don't totally follow what you have done, nor which OS you are trying, but can not manage to boot.  Is it an OS or just an iso file on the USB drive?  Is your OS on an internal hard disk, but grub now missing from both that and the USB?

More details please.

---

### Post by happyslurpies on 2012-10-10
GRUB (the bootloader) is on the drive  - I don't need to configure it directly.
 
The problem is that the LiveCD of Ubuntu (the OS just in memory, not permanently installed per se) will not boot anymore because I, as I said, changed a setting on the LiveCD of Ubuntu, and now it won't boot anymore.
 
I used this program to automatically combine the bootloader (I don't know which version of GRUB it was) with the .iso of Ubuntu on the USB: [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)
 
I can't get on the LiveCD, no. It has to do with BIOS (obviously) not finding GRUB due to the change I made with the file system and/or the hexadecimal address of the such.
 
As long as the address is wrong, I'm getting nowhere(where will BIOS jump to if it's wrong?).
 
If it isn't clear by now, no, I can't even boot the LiveCD. That's the whole purpose of this post. If the LiveCD worked I'd have no reason to start a topic with "booting Ubuntu" and not finding boot settings naturally

---

### Post by oldfred on 2012-10-10
An install to a flash drive usually does not use grub2's boot loader but uses syslinux.

You have to have a way to boot. If that is Windows I do not know how to repair from Windows. But you mention another computer with Linux. So can you not plug into the other computer and run Boot Repair or reinstall the boot loader to the flash drive?

---

### Post by ajgreeny on 2012-10-10
Sorry, but you have now lost me totally!  I will therefore withdraw from this thread's conversation.

Oldfred is usually very good at sorting out such difficulties, so I'll leave you in his safe hands.

---

### Post by oldfred on 2012-10-10
I am somewhat lost also, as without a Linux to boot, it is difficult to tell what the issue is. We need to be able to run something from another working system to report what is wrong.

If it is just the installer, then a reinstall is the quickest & easiest way to fix it.

---

### Post by happyslurpies on 2012-10-11
I have another computer I can access with Windows installed.
 
However, I'm not sure on how I can fix the problem with BIOS failing to jump to the bootloader.
 
All I can think of is to remove all of the file system files from the drive, and redo everything(the bootloader, disc image, etc.).
 
Clearly no one here understands or has faced this issue before.
 
I guess thanks for bothering to help at least ... though it appears that I'm going to have to (as always) fix the problem entirely myself.

---

### Post by oldfred on 2012-10-11
ajgreeny's suggestion of Boot-Repair would probably have fixed it. That was 4 days ago.

 Boot-Repair can be installed in any other working Linux liveCD or has its own liveCD as a Linux repairCD which is always good to have anyway. 

I typically have Boot-Repair, SuperGrub, gparted all as liveCDs on one flash drive as well as Knoppix, several versions of Ubuntu. And I often have a current LiveCD as another way to boot just in case flash drives stop working for some reason. You cannot have too many repair tools in your tool box.

---

