---
title: "How to: Dual boot Windows 8 and Ubuntu 13.10 on Samsung 900X3E"
date: 2013-09-24
forum: Hardware
---

### Post by hayo.hase on 2013-09-24
I am(was) unfamiliar with Windows 8 and Ubuntu >10.04LTS. Hence it was quiet a challenge to get my new notebook Samsung NP900X3E -A01DE ready for dual boot. I exercised one week with some frustrating moments and here I summarize what was successful in the end. 

1. Become familiar with some basic functions of the pre-installed Windows 8 system. Read also about UEFI to understand the new boot concept, which you will find on any Windows 8 computer.

2. Start Windows 8, have a network connection and update the firmware of your Samsung machine. Find on the Windows tile screen the "Samsung Apps - SW Update". This will download and install the latest firmware for your computer hardware, I think also for the BIOS itself. This is import, as this machine uses UEFI to support Windows 8.

3. After the firmware update you should reboot a couple of times (at least twice!) and see if everything works under Windows 8.

4. Make space for Ubuntu on the SSD disk under Windows 8. Press "Windows"-"X" buttons simultaneously and select "Diskmanagement". If the computer is brand new, you can apply shrinking largest partition in order to make space you want for Linux. You will need later at least 20GB for Linux and 1.5-times the RAM size as swap partition. I have a 512GB disk and made 256GB available for Linux including the swap space of 7GB. 
If the computer is used, make first a backup of your data and defragment the disk. Do not reduce the size too much. Don't format the new disk space, we do that from Linux.

5. Still under Windows 8, download the latest ubuntu distribution, at least 13.10. (Older versions may show ugly lines on the screen.) 
Find the latest iso-image on [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/) (if you can't find anything newer than 13.04 on the ubuntu download page). You will need a newer Kernel than 3.10. Ubuntu 13.04 comes with kernel 3.8 and is not good enough.
 Chose the 64-bit desktop version and download it. I.e.  [saucy-desktop-amd64.iso]("http://cdimage.ubuntu.com/daily-live/current/saucy-desktop-amd64.iso")  

6. Have a >2GB USB pendrive available (with no data). Create a bootable USB pendrive by copying the iso-image from the previous step to the USB-stick. 
Use the Universal-USB-Installer: [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)
Now you have a bootable ubuntu USB-stick.

7. Shut off Windows. Put your bootable USB-stick in.

8. Switch on your computer and press immediately F2. You will enter the BIOS.
Go to "Advanced" and disable "Fast BIOS Mode".
Go to "Boot"-"Boot Device Priority" and move your pendrive into the first position. 
Check if "Secure Boot" is enabled. Ubuntu supports it. Other Linux versions might not do it (I had no luck with Linux-Mint).
F10 - save and exit.
Now the Ubuntu system should boot. Select first the Ubuntu trial (live system), which does not do any change to the hard disk.

9. Now we are working under Ubuntu. The live-system comes with gparted to format the partition for Ubuntu (>20GB) and a swap partition (1.5 times RAM). Use the space available which was obtained in the previous step 4. No boot partition is needed, as ubuntu will share the already existent EFI partition with Windows after installation.
[https://sites.google.com/site/easylinuxtipsproject/partitioning](https://sites.google.com/site/easylinuxtipsproject/partitioning)
The "/" partition should be formatted as "ext4" and "swap" should appear as "swap".
You may want to explore ubuntu for a while on your computer, check out the network function, start libre office for display checks etc., before rebooting it again.

10. After reboot from the USB-stick we select this time "install" and do not start the live-system. (I had no luck with installing Ubuntu from inside the live-system.)
If you are connected to the internet, newer software package versions will be installed (this is time consuming). But this can be done also later.
The installation process is straight forward - just be patient. Make a user account. The first user has administration privileges.
When finished you will have to restart and take off the USB-stick during the reboot cycle.

11. When the computer starts again, press immediately F10 and the BIOS offers you to either boot "Windows" or "ubuntu".
Select "ubuntu", GRUB2 will start, select Ubuntu once again and the login-screen of ubuntu should appear. Login and continue with software installations and configuration.

12. For future boots use always F10 after switching the computer on. The alternative would be to use F2 instead, but then you have to go there to "Boot"-"Boot device priority" and make the change to your priority.


I still haven't explored yet, which further configuration settings are necessary to have all the features like under Windows available (lifetime extending mode by charging the battery only 80%, regulate the dimming of the keyboard lights, fan noise regulator, etc.). I hope this description prevents you from going through one entire recovery cycle of Windows 8 (which was my case, when I got the BIOS settings wrong) and be disappointed about a brand new machine displaying missing pixels in horizontal lines across the screen (when I used ubuntu 13.04).

---

### Post by oldfred on 2013-09-24
A lot of users installing seem to have various video issues. Did you have any and what video do you have?

---

### Post by hayo.hase on 2013-09-26
I guess that you refer with "video" to the graphic card of the Samsung 900x3e. It has only one build-in graphic card Intel HD Graphics 4000.
I am still testing and so far I had no problems watching html5 video under chrome. (My firefox without html5 add-ons does not, but shows video streams of news-channels, such as tagesschau.de, without problems.)

---

### Post by doyleed on 2013-10-26
THANK YOU so much for your excellent post.  I just bought a Samsung ATIV Book 8 (and I love it).  I followed your procedure and now it is perfect, dual boots Windows 8 (now 8.1 after I did the upgrade) and Ubuntu 13.10.  One quick comment that 'may' help others.  I used the Windows Disk Management tool to shrink the C: drive to make  space for Ubuntu, just as you suggested.  Although the drive had 900+G free, the Windows tool would only allow me to shrink it about 430G.  Before shrinking, I used gparted in the Ubuntu live USB drive to look at the C: partition.  gParted was perfectly willing to let me shrink it 900G, but I decided not to do it.  Then I used uldefrag in Windows to look at the C partition, and I could see some unmovable data in about the middle of the C drive.  I do not know what would have happened if I had chosen to let gparted shrink the partition, but I decided not to find out right now, so I followed your advice and used the Windows disk management tool.  The only other thing I might add to your perfect procedure is just to emphasize what you say, turn off fast boot during the entire procedure.  Turn it back on after completing everything above and leave it on.  Also, I would emphasize to make the boot loader be /dev/sda# where # is the number where you are installing Ubuntu.  IF you leave it as /dev/sda with no number, you will overwrite the mbr, and although I did not try it, I presume Windows would not boot. I use the F10 approach, just as you suggested, to get to the grub menu, or do nothing to boot in Windows after a fresh start.  Well, again - THANK YOU very much for your procedure.  It worked perfectly for me the first time - no hitches.

---

### Post by oldfred on 2013-10-26
@doyleed
Ubuntu installs in the mode you boot install flash drive, either UEFI or BIOS/CSM.

If in UEFI mode grub only installs to the existing efi partition. I think that is the default in UEFI mode.

But if in BIOS/CSM/Legacy boot mode, then the only way you can boot is in CSM mode (UEFI turned off in UEFI) and from the gpt's protective MBR. You cannot install grub2's boot loader to the Ubuntu partition and have a bootable system.

---

### Post by martinr on 2013-11-09
> **oldfred said:**
> @doyleed
Ubuntu installs in the mode you boot install flash drive, either UEFI or BIOS/CSM.

If in UEFI mode grub only installs to the existing efi partition. I think that is the default in UEFI mode.

But if in BIOS/CSM/Legacy boot mode, then the only way you can boot is in CSM mode (UEFI turned off in UEFI) and from the gpt's protective MBR. You cannot install grub2's boot loader to the Ubuntu partition and have a bootable system.

Just make sure that you don't boot the installation CD with a UEFI boot sequence if your HD structures is MSDOS with MBR or vice versa.
(See: [this thread]("http://ubuntuforums.org/showthread.php?p=12030957#post12030957"))

What did your HD structure turn out to be?

---

