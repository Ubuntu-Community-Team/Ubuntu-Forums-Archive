---
title: "A serious mess of my hard drive!"
date: 2010-08-03
forum: Hardware
---

### Post by jedimattk on 2010-08-03
I feel like I've completely locked myself out of my own computer. The whole story is long and boring, but basically Windows 7 has been bugging out and irritating me, so I decided to switch back to Ubuntu. In the past I've done this by booting from a live CD; on this laptop, my CD drive rarely works the way it should, so more recently I've done it by booting from a live flash drive.

Neither of these options worked this time, though. In the case of the live CD, my computer didn't even recognize its existence and breezed right over it. In the case of the live USB, it just gave me an unhelpful "BOOTMGR is missing, Ctrl+Alt+Del to restart" message and refused to go any further. Yes, my boot process is correctly configured. Yes, the disc and the USB were both burned correctly (the former at 2x speed through Nero on a separate computer with a working drive, and the latter using UNetBootin.) 

Despairing of my chances, I booted back into Windows, which I found did indeed recognize the live CD in the drive (even though it wouldn't boot from it.) I decided to install Ubuntu using Wubi into its own little 10GB partition, thinking that I would later just format the Windows partition away and expand the Ubuntu partition to fill the whole hard drive.

No dice. Oh, Ubuntu installed, but what I failed to realize was that I couldn't do any formatting from within Ubuntu because the hard drive would be mounted. Now I barely have a megabyte to spare on my hard drive, and I can't boot from anything but said hard drive. I have live CDs for various versions of Linux, gParted, even DBAN, but it's irrelevant because **I can't load any of them.**

Because I'm working on a laptop, I have no viable way of taking out the hard drive  and connecting it to another computer for formatting... so I'm stuck, guys. I'm really stuck.

---

### Post by Fafler on 2010-08-03
Try remaking the bootable flash drive from within Ubuntu with System -> Administration -> Startup Disk Creator. Erase the drive first.

---

### Post by jedimattk on 2010-08-03
Didn't work. More specifically, it wrote to the USB drive and booted from it without issue, but /dev/sda1 (my hard drive) is still mounted. There is no apparent way to unmount it either, even from the live USB environment.

---

### Post by sikander3786 on 2010-08-03
Hi.

Are you able to login into either Windows or Ubuntu or both? If you can boot into Windows you will easily be able to uninstall WUBI which in return will give you your HDD space.

Does you CD-ROM boot any CD? Any partitioning software or Windows CD? If it boots then you should consider formatting and reinstalling either Windows or Ubuntu or any Distro.

---

### Post by DrMelon on 2010-08-03
From the live USB, you should be able to unmount the harddisk by using:
```
sudo umount /dev/sda1
```
That should force it.

---

### Post by prshah on 2010-08-03
> **jedimattk said:**
> In the case of the live USB, it just gave me an unhelpful "BOOTMGR is missing, Ctrl+Alt+Del to restart" message and refused to go any further. 

> **DrMelon said:**
> From the live USB, you should be able to unmount the harddisk by using:
```
sudo umount /dev/sda1
```
That should force it.

The error message you have mentioned is an Windows error message; it has nothing to do with your Linux; essentially, the linux bootloader has been skipped.

You can try changing the USB device type in the BIOS; most systems have options similar to USB:HDD and USB:FDD. I think your type will be set to USB:HDD; try setting it to USB:FDD and see if you can boot off your live USB. Alternately, toggle the "USB Legacy" setting.

Some laptops (esp netbooks) only allow particular USB ports to be used for bootup; please see your manual, or look for settings such as USB0, USB1, USB2 in the bootup order options.

If you manage to boot off a live USB, you need to unmount any mounted HDD partitions, as well as turn off swap ```
sudo swapoff -a
``` before you will be allowed to make any changes.

Please post back with results if you need more help,

---

### Post by jedimattk on 2010-08-03
I booted back into the live USB environment and tried your terminal command, "sudo umount /dev/sda1". It was a calamitous failure:

> umount: /cdrom: device is busy.
(In some cases useful info about processes that use
the device is found by lsof(8) or fuser(1))

My computer is not booting from anything else. It doesn't recognize CDs, USBs, anything (apart from this Ubuntu startup disk I made.) I can log into both Windows and Ubuntu just fine, but the objective here isn't to uninstall Ubuntu and go back to how everything was set up before; it is to have Ubuntu as the sole OS on my hard drive.

---

### Post by mortenmeldal on 2010-08-03
Hi try this:

Open your PC and unplug the SATA cable from the HD.
Start the PC with the Ubuntu installation CD/DVD in the drive.
Insert the SATA cable again immidiately once the Ubuntu package has the control of the PC. Allow Ubuntu to partition your HD and install Ubuntu.
That worked for me.
You will loose all currently on the HD.

If it wont work immediately then you may format your HD first then do the same as above. The trick is to give Ubuntu the boot control

Regards
MPM

---

### Post by jedimattk on 2010-08-03
Well, I'm on a laptop. It's probably possible to go in and mess around with SATA cables, et cetera, but I don't know how and frankly don't want to.

---

### Post by oldfred on 2010-08-03
From windows can you make a FAT32 1GB partition? If you have a separate 1GB partition you then can install from that as all the other partitiion(s) can be unmounted. Think of the 1GB partition as a USB. You will have to have grub in the MBR to boot the partition. Install grub2 and put the ISO on the partition just like on a USB drive.

It would be a combination of USB & direct boot from hard drive. 
 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
[http://www.pendrivelinux.com/install-grub2-on-usb-from-ubuntu-linux/](http://www.pendrivelinux.com/install-grub2-on-usb-from-ubuntu-linux/)

[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864&highlight=ISO](http://ubuntuforums.org/showthread.php?t=1535864&highlight=ISO)

---

### Post by prshah on 2010-08-04
> **jedimattk said:**
> "sudo umount /dev/sda1".

umount: /cdrom: device is busy.

According to this error, it seems as though your CDROM drive is /dev/sda1 (!!); though I have never seen anything like this (I suspect a typo somewhere), please confirm your HDD device with the command```
sudo fdisk -l
``` from the live USB environment.

Please post back the output for a look.

---

### Post by jedimattk on 2010-08-04
I know! It confused me too, and I couldn't find any precedent to a situation like this. But I've been screwing around with it for the past couple days and now have a clean Ubuntu 10.04 install on my hard disk. I really have no idea what I did differently - just went back into Windows, uninstalled Wubi, and kept fiddling with different ways to boot Ubuntu live until I found one that worked.

Anyway, this problem is resolved now, but another one has cropped up. (Isn't that always the case?) Ubuntu has randomly shut down on me twice throughout the day, and I have no idea why. If you might be able to help, refer to the new thread [here](http://ubuntuforums.org/showthread.php?t=1546143).

Thanks again!

---

