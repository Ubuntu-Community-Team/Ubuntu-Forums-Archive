---
title: "Boot ubuntu 17.04 from ssd nvme"
date: 2017-04-21
forum: Hardware
---

### Post by kalindimitrov on 2017-04-21
I want to install ubuntu 17.04 on my new desktop which will use samsung 960 evo. Is it possible to boot from ssd with nvme in this version of the kernel (4.10)

---

### Post by oldfred on 2017-04-21
It should work.
But many threads where users had to update UEFI/BIOS or firmware on SSD to get it to work.
Initial support has been there for several years.

 gparted should be at least version 0.24.0-1 to recognize NVMe devices
[http://gparted.sourceforge.net/index.php](http://gparted.sourceforge.net/index.php)
Filesystem support
[http://ubuntuforums.org/showthread.php?t=2318570](http://ubuntuforums.org/showthread.php?t=2318570) 
      
 Support for NVMe in grub-mkdevicemap fixed in 2014
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1275162](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1275162)
spec entry for nvme devices (UEFI v2.4A 9.3.5.22)
[https://ubuntuforums.org/archive/index.php/t-2292993.html](https://ubuntuforums.org/archive/index.php/t-2292993.html)

---

### Post by kalindimitrov on 2017-04-21
Ok. thanks. How I can update firmware of the ssd before I install the OS

---

### Post by oldfred on 2017-04-21
Best to check with vendor of SSD.
Have never done it for SSD, just for UEFI.
This says we should check every year:
 [https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd) 


What brand/model desktop or what motherboard?
And what video card/chip?
Many seem to need various settings in UEFI or boot parameters.

---

### Post by kalindimitrov on 2017-04-21
I'm not sure if you ask me. But my motherboard is Asrock taichi x370
[http://www.asrock.com/mb/AMD/X370%20Taichi/](http://www.asrock.com/mb/AMD/X370%20Taichi/)
It's pretty new and im sure that i'm in troubles but anyway.  The video will be amd rx 460

---

### Post by oldfred on 2017-04-21
Your hardware is the very newest. And typically it takes a while before all the needed bits & pieces are in a standard distribution.
You at very least need newest Ubuntu and may still have to download newer kernel & drivers. 

Older Asrock used Asmedia ports for extra drives. They cause issues and cannot be used even for a DVD. 
Yours may not even have the Asmedia.
 Asrock Z170 ASmedia port issue
[https://ubuntuforums.org/showthread.php?t=2345564](https://ubuntuforums.org/showthread.php?t=2345564)
 Asrock Z97 w/Core i7 5775C tried the "CPU OC Fixed Mode" of the ASRock UEFI setup.
[URL="http://www.phoronix.com/scan.php?page=news_item&px=Core-i7-5775C-OC-Fixed-Mode"]http://www.phoronix.com/scan.php?page=news_item&px=Core-i7-5775C-OC-Fixed-Mode

[/URL]
 Trying AMDGPU-PRO 17.10 On Ubuntu 17.04 (does not work directly)
[http://www.phoronix.com/scan.php?page=news_item&px=AMDGPU-PRO-Ubuntu-17.04](http://www.phoronix.com/scan.php?page=news_item&px=AMDGPU-PRO-Ubuntu-17.04)
[https://help.ubuntu.com/community/AMDGPU-PRO-Driver](https://help.ubuntu.com/community/AMDGPU-PRO-Driver)
AMDGPU-PRO 17.10 Released With Ubuntu 16.04.2 Support
[http://www.phoronix.com/scan.php?page=news_item&px=AMDGPU-PRO-17.10](http://www.phoronix.com/scan.php?page=news_item&px=AMDGPU-PRO-17.10)
AMDGPU & Radeon DDX Updated - Better 2D Performance, Tear Free, DRI3 Default Nov 2016 

[URL="http://www.phoronix.com/scan.php?page=news_item&px=Core-i7-5775C-OC-Fixed-Mode"]
[/URL]

---

### Post by paulisdead on 2017-04-21
Shouldn't be a problem.  I've got the Crosshair Hero VI, which is the same chipset as yours.  My bootloader and /boot/efi are running off the nvme drive, and ubuntu 17.04 sees it fine, although I'm running root off a 480GB sata ssd and gave the nvme drive to windows.  The nvme drive is an intel 600p.  From Ubuntu I can browse the nvme drive, so it's working fine.

If you want to update SSD firmware, it varies from manufacturer to manufacturer, but a lot only provide windows utilities to do it.  So you'd probably have to be able to plug the drive into a windows system and run their tool on it, but check with the manufacturer's directions.

---

### Post by kalindimitrov on 2017-04-22
Is your sound card work properly with kernel 4.10 ?

---

### Post by paulisdead on 2017-04-22
I never bothered to try it, I've got an Asus Xonar DX I've been perfectly happy with, so I carried it over.  I do know the ALC1220 sound chipset didn't get supported until kernel 4.11, so you should probably look at upgrading, which is part of the reason why I just stuck with the sound card I've been using.  There's a ppa with newer kernels around so it should be super easy.

---

### Post by kalindimitrov on 2017-04-22
sound work :)

---

