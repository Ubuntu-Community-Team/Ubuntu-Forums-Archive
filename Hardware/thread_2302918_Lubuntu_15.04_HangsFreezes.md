---
title: "Lubuntu 15.04 Hangs/Freezes"
date: 2015-11-14
forum: Hardware
---

### Post by rumble16 on 2015-11-14
Hello,
I have been struggling to install a Linux OS on my computer for about a week now. The installers repeatedly failed, either throwing errors or simply freezing in the middle of operations. Eventually I wiped the drive entirely using a windows recovery CD, put a GPT partition table on the drive with Gparted, then used the entire disk for Lubuntu 15.04. I used the alternative, text-based installer and it did not give me any errors and it did not freeze. Once installation was complete, I was relieved that my problems were coming to an end.
However, I am experiencing the same freezing issue with the installed OS as I was having with the live CD. I did not realize that my issue was related to the hardware on my computer, rather than the software on the disk.
I read a couple related threads and attempted to find the hardware that is causing the problem. So far, I have removed my wireless adapter, and disabled my Ethernet controller, but neither of these things solved the problem. I noticed that the computer still plays sound when it crashes, so I am fairly certain that it is a graphical problem.
I ran these commands after booting the computer to change the graphics driver
sudo apt-get install fglrx
some related updates for fglrx
The problem persists. I have a feeling that I did something incorrectly, but since I am new to Linux, I am at a loss.
The hardware details of my computer are as follows:
GA-970A-UD3P motherboard
AMD-FX4350 CPU
Radeon R9 270x graphics
1.0 TB HDD
8.0 GB RAM
wireless PCIe device
I would really appreciate some help getting the system running.
Thank you in advance.

---

### Post by mörgæs on 2015-11-15
How does 15.10 work?

---

### Post by rumble16 on 2015-11-15
I have tried ubuntu 12.04.5, 14.04.3, and 15.10. I have also tried Lubuntu 14.04, 15.04, and 15.10. They are all experiencing crashes and freezes. Just today I installed Linux Mint 17.2, and it, too was freezing. I disabled IOMMU in the bios, and haven't had a freeze since then. However, the installer will not install Linux Mint onto the HDD, throwing errors like "Failed to create a swap space at /dev/sda3" or "failed to mount file system type ext4 at /dev/sda2." I think that I will start a separate thread dealing with that issue.
Apparently the freezes were not graphically related.
As far as I am concerned, I am blaming IOMMU for the freezing/crashing and moving on to the next problem which prevents me from installing linux.

---

