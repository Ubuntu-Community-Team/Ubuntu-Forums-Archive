---
title: "Interesting / Annoying Install Problem"
date: 2009-07-30
forum: Installation &amp; Upgrades
---

### Post by wildmanmatt on 2009-07-30
Hi,

I am trying to install 9.04, but encountering an annoying error.

I am running on an 
MSI K9N SLI Platinum nForce 570 SLi motherboard
with an
AMD Athlon 64 X2 5600+ processor
and an
Asus EN8800GTS/HTDP/320M 8800GTS 320MB DDR3 DVI-Ix2 HDTV PCI-E graphics card
I have 
8GB of RAM
and
5.3TB hard disk space (across 7 hard drives)

I have tried both Ubuntu and Kubuntu flavours and the problem occurs with both.

When running the install with the default options but removing the splash, the install hangs on
[0.910653] pci 0000:00:00.0: Enabling HT MSI Mapping

However, when I press F6 and disable acpi in the boot options, I can get into the live version and into the installer (both from within the live and direct from the CD), but two of my hard drives are not detected. 

Out of the 7, I have 2 1TB SATAs, 1 1TB USB, 2 750GB SATAs, a 500GB SATA and a 320GB SATA.
The ones that are detected are 1 of the 1 TB SATAs, the 1 TB USB, the 2 750GB SATAs and the 500GB SATA.

It is the 1TB SATA that is not detected that I want to install onto. It is the same make and model as the one that is detected.

I have booted up in GParted Live and the hard drive is detected then as well as being detected in the Vista installer (I loaded it to check) and is detected by OpenSUSE 11.1 (I tried to install that when I ran into these problems with Ubuntu, and altough everything installed perfectly, I had major problems with OpenSUSE, KDE and my Nvidia graphics card...which I don't seem to have with Ubuntu - if only I could get the thing installed!)

If someone had some suggestions of what I could try, it would be much appreciated...

Thanks,

Matt

---

### Post by ajgreeny on 2009-07-30
Does gparted in the ubuntu live CD see the drives or is the gparted you booted to a gparted live CD?  If the latter, try the ubuntu live CD which also has gparted on it, just to find out whether or not ubuntu can see those two disks at all.  You can also run ```
sudo fdisk -l
``` from the live CD to see if that sees them.

---

### Post by wildmanmatt on 2009-07-30
It was a gparted live CD that I used

Running sudo fdisk -l on the ubuntu live cd (after starting with acpi off and no splash screen) just brings up the 5 drives, so for some reason Ubuntu can't see 2 of them... (and I don't think there's anything special / out of the ordinary about them... they're on the same controller as the other 4 SATAs that have been detected)

---

### Post by presence1960 on 2009-07-30
have you tried the [alternate text based installer]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate")?

---

### Post by lethalswc on 2009-07-30
Hi, I am also having a little trouble. I originally tried to install Ubuntu 9.04 using the live cd to no avail. This resulted in the error at boot. "no boot device available" and I have tried to locate and fix the mbr using the ubuntu os and I also tried to mount grub in the mbr using the super grub disk. I eventually gave up and reinstalled windows. 

Now after a clean install of windows I ran the live cd again, and this time I created a partition for a dual boot with ubuntu. After restarting the computer the windows booted up as normal. I assumed that the install was unsuccessful and ran the live cd again but the ubuntu partition is still there. Why is the option not coming up during boot for ubuntu. 

I am running a Dell E510 (5150) with the oem software raid configuration and 2 250G with 2 SATA Drives and my OS is Windows XPME. Any info needed please ask.

Sorry if my post is unclear but I am just learning about this and I would like to start using ubuntu.

Thanks in advance.

---

### Post by presence1960 on 2009-07-30
> **lethalswc said:**
> Hi, I am also having a little trouble. I originally tried to install Ubuntu 9.04 using the live cd to no avail. This resulted in the error at boot. "no boot device available" and I have tried to locate and fix the mbr using the ubuntu os and I also tried to mount grub in the mbr using the super grub disk. I eventually gave up and reinstalled windows. 

Now after a clean install of windows I ran the live cd again, and this time I created a partition for a dual boot with ubuntu. After restarting the computer the windows booted up as normal. I assumed that the install was unsuccessful and ran the live cd again but the ubuntu partition is still there. Why is the option not coming up during boot for ubuntu. 

I am running a Dell E510 (5150) with the oem software raid configuration and 2 250G with 2 SATA Drives and my OS is Windows XPME. Any info needed please ask.

Sorry if my post is unclear but I am just learning about this and I would like to start using ubuntu.

Thanks in advance.

I am not versed in raid, but I do know the Live CD does not have support for raid. You need to use the [alternate text based installer]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate")

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)  scroll down to the section Installing on external or raid hard disks

---

### Post by lethalswc on 2009-07-30
Ok 

I will try it now thank you for the quick reply. I will let you know wat happenned. Thanks.

---

### Post by wildmanmatt on 2009-07-31
The problem was solved by using the alternate install CD and the nolapic boot flag. However, I now have the following networking issue that I have posted about [here]("http://ubuntuforums.org/showthread.php?p=7711038#post7711038")

Thanks for your help presence.

Matt

---

### Post by presence1960 on 2009-08-01
you are welcome!

---

