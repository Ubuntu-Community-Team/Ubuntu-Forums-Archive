---
title: "SSD not being detected"
date: 2017-03-25
forum: Hardware
---

### Post by droplo on 2017-03-25
Hey guys,

To start things off, here are my system specs:
Intel i7-7700k
Asrock Z270 Killer SLI/AC motherboard
MSI Geforce GTX 1070 Gaming X
Corsair Vengeance LPX 16GB(8x2) @ 3000 mhz
NZXT Kraken X52 water cooler
Samsung 850 EVO 120gb
Samsung 850 EVO 500gb
Corsair RM750x power supply

Everything is new besides the graphics card and SSD's which i bought used, i have no idea if anything is on the SSD's.

At the moment i only have my 120gb ssd plugged in, and am trying to install Ubuntu on my PC using a disk, My SSD is being detected fine in my bios from what I can tell, but when i go to install Ubuntu, it says i have 0.0bytes disk space. So I went into Ubuntu live and open GParted, the only drive showing is my DVD drive, not my SSD. I've tried switching the cables from my SSD and DVD drive but the same thing happens, only the DVD drive shows up. I am unsure what to do, I will give links to images of my bios screen showing my SSD configuration.

[http://i.imgur.com/ozwGm4n.jpg](http://i.imgur.com/ozwGm4n.jpg)
[http://i.imgur.com/5OZ0pgp.jpg](http://i.imgur.com/5OZ0pgp.jpg)
[http://i.imgur.com/o92wGZp.jpg](http://i.imgur.com/o92wGZp.jpg)

---

### Post by droplo on 2017-03-25
[http://i.imgur.com/kJCsfsB.jpg](http://i.imgur.com/kJCsfsB.jpg)
This is the command window that appears directly after launching Ubuntu without installing. Looks like a lot of things fail and it seems wrong to me

---

### Post by Autodave on 2017-03-25
First thing I would try is the other SSD: seems to me that the current one is no good. However, I am NOT an expert at looking at your screen shots.  But, it is a simple thing to try another HD and be sure.

---

### Post by droplo on 2017-03-25
ive tried both of my ssd's and unfortunately had the same result with both. I don't have any others either..

---

### Post by ajgreeny on 2017-03-26
Does the disk have a partition table on it yet or is it totally blank?
Did you go to the drop-down box top right in gparted to see if the device is detected?

Which version of Ubuntu are you trying to install?
There appear to have been some problems with 14.04 Trim settings but 16.04 should be fine as far as I can see from a quick search.
Make sure you booted the install medium in either UEFI or BIOS depending on your machines setup, which I imagine from your images is UEFI, as that can cause problems detecting disks/partitions if you get it wrong.

---

### Post by droplo on 2017-03-26
I had checked the drop down menu in gparted and the ssd doesn't show. I also went into disks and it showed something was plugged in, but did not give me any information on it. The info screen just said "no media" and it was just labeled "disk". 

I am also trying to install windows 10 with no avail. It seems like the SSD is not being recognized by either OS. It doesn't show up in Gparted in ubuntu, nor Diskpart via CMD in windows. I had it show up once in diskpart and I was shocked by it and unplugged it to see if it was actually it.. It was.. and since then after rebooting and repeating everything I had done diskpart will not show it again. I downloaded samsungs driver downloader .exe on a flash drive and tried running it manually through the CMD but says it isn't supported by my version of windows. It still shows up in my bios. But nowhere else. Not in ubuntu or windows and I don't know what to do. Since I bought them used i have no idea if anything is on them. I can't detect them at all except in bios. 

I just bought a 500gb HHD from amazon to see if i can just download windows onto that and troubleshoot my SSD's after..

---

### Post by oldfred on 2017-03-26
Are you using Asmedia port(s)?
All older Asrock have those ports and if anything including  a DVD is plugged into an Asmedia port it causes issues.

 Asrock Z170 ASmedia port issue
[https://ubuntuforums.org/showthread.php?t=2345564](https://ubuntuforums.org/showthread.php?t=2345564) 

Are you using internal Intel video, or nVidia to boot?
You may need nomodeset.

      
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

And you will probably need the updated video drivers from the ppa once installed.
       
 Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
sudo apt-add-repository ppa:graphics-drivers/ppa

---

### Post by Yellow Pasque on 2017-03-26
I would try a different SATA cable and header. Also, on an unrelated note, it looks like you installed the memory sticks in the wrong slots if you want dual channel operation (and you probably do). They either need to be in slots A2 and B2, or in slots A1 and B1.

> Are you using Asmedia port(s)?

From looking at the manual, I don't think this board has an Asmedia chipset. It just has the 6 SATA headers from the Z270 chipset.

---

