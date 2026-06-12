---
title: "Is there a way to dual boot Windows 7 and Ubuntu in a Lenovo Ultrabook (with ssd cach"
date: 2013-03-04
forum: Hardware
---

### Post by THPubs on 2013-03-04
I have seen many people trying to install Ubuntu on laptops like the Lenovo U410 and Samsung Series 5 ultrabooks fail. Sometimes,we have to give up the SSD cache. Have the developers solved it now? Can we install Ubuntu on an Ultrabook like U410 without loosing the SSD cache?


Links to the issue :


[http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/Lenovo-U410-Cannot-access-to-BIOS/td-p/877703/page/2](http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/Lenovo-U410-Cannot-access-to-BIOS/td-p/877703/page/2)
[http://forums.lenovo.com/t5/Linux-Discussion/Installing-Ubuntu-12-04-on-Ultrabook-U410/td-p/871873](http://forums.lenovo.com/t5/Linux-Discussion/Installing-Ubuntu-12-04-on-Ultrabook-U410/td-p/871873)
[http://ubuntuforums.org/showthread.php?t=2023374](http://ubuntuforums.org/showthread.php?t=2023374)


Here's one problem :


> I recently bought a U410 ultrabook. With the factory settings, the ubuntu installer does not detect any disks on the system. The problem is known and has something to do with the SSD, Intel Smart response technology and the disks' RAID configuration (See Unable to install 12.04 on a Lenovo U410 Ultrabook and [http://ubuntuforums.org/showthread.php?t=1825132](http://ubuntuforums.org/showthread.php?t=1825132))


Is there a way around this problem without having to remove the existing Windows installation? Also in case not, does my warranty get void if I remove the pre-loaded windows installation? An Ubuntu system is essential for me so I need to get it installed somehow.


Would appreciate some pointers.


The only solution is to disable SSD cache and install windows to SSD (I don't think 24GB will be enough) :


> Disabe RAID (select ACHI in BIOS)
Install windows to SSD.
Move user data and pagefile to HDD. Disable file indexing on SSD. Install most not system programs to HDD to economy free space. It will be even faster than cache, but you need to install big programs and games on D:. Not every man can do it. Thats why they use cache as default.
Boot Ubuntu from CD, type in terminal "sudo apt-get remove dmraid"
Install Ubuntu as usual
If GRUB doesnt appear (it is because of UEFI) use Boot-Repair utility as described here [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
If GRUB appears, but Ubuntu doesn't boot, then you need to break dmraid utility:


7.1 Boot Ubuntu from CD


7.2 type in terminal "sudo apt-get remove dmraid"


7.3 Open "Computer" on the desktop and open the disk where you have installed Ubuntu. On the top of the window will be some letters like 7bgetgu4uf87wch7wir6. Type in terminal "sudo rm /media/{your partition}/sbin/dmraid" where you replace {your partition} with this letters


7.4 "sudo touch /media/{your partition}/sbin/dmraid" and "sudo chmod +x /media/{your partition}/sbin/dmraid"


Once you have booted ubuntu, remove dmraid in normal way (using apt-get)


And the easy way is to install ubuntu with wubi. I tried it on ACHI, but there was no problems with dmraid and grub


Here's another problem :


> So i bought a lenovo u410 the other day to use with linux along side my windows pc, problem is when i get to the installation screen the hard drives dont show up (500gb hdd or 32gb ssd) i also took off acceleration and put the hard drives in non raid mode but that still didnt work, i also tried wubi to see if it would run for kicks but that wont work either, can anyone help me out?


---

### Post by psaxena on 2013-04-04
Seems like there isn't something yet.

I am waiting for a solution to the same problem. Unable to use my six month old Lenovo U410 properly.

---

### Post by oldfred on 2013-04-04
some others who had various amounts of sucess.
  lenovo u310  - install to SSD
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)
Lenovo IdeaCentre K410 Pentium 64-bit
[http://ubuntuforums.org/showthread.php?t=2129961](http://ubuntuforums.org/showthread.php?t=2129961)
> Discovered that on my Lenovo, if I press F12 repeatedly on startup, it takes me into a Boot Order menu. If I select Windows there, it boots into Windows. I also found that to get into BIOS at startup on my Lenovo tower, you press F1 rather than the F2 I'm used to on other computers.

Intel SRT is a standard and implementation is almost identical for all vendors.
      
  Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)
ubuntu 12.10 & Windows 8 oem Sony T & Intel SRT
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)
Intel SRT - Dell XPS Screen shots of Intel SRT screens & lots of details 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
Details in post #10 on an install that worked
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)
Dell XPS Intel SRT issue on hibernating post #25
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)
Some info on re-instating  details in post #9 Dell 14z
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
Disable the RAID, it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

---

