---
title: "install on secondary drive"
date: 2009-04-12
forum: Installation &amp; Upgrades
---

### Post by richlyn9 on 2009-04-12
I want to install ubuntu on a secondary drive while having XP on the primary drive.i will be able to install the OS but i am concerned of whether i will get the option to boot ito the OS since the XP is on the primary and linux on the secondary.can somone please help me regarding this.

---

### Post by Partyboi2 on 2009-04-12
You will have the choice to be able to boot into either operating systems even if they are on separate hard drives.

---

### Post by Ticketoride on 2009-04-12
> **richlyn9 said:**
> I want to install ubuntu on a secondary drive while having XP on the primary drive.i will be able to install the OS but i am concerned of whether i will get the option to boot ito the OS since the XP is on the primary and linux on the secondary.can somone please help me regarding this.

If you leave both Drives physically connected to your Computer and you install Linux to your second Drive, Linux will provide a Boot Loader where you can opt to boot into either operating System. In this Fashion Linux installs some Files on your bootable Windows Partition in order to load the Boot Manager.

If you ever re-install Windows or upgrade to a later Version, Linux will no longer boot and you will have to go through some complicated Routines to put the Linux Bootmanager back after, a Procedure often beyond the skill or capability of your average User not reasonably well-versed with Linux.

The second Method is to physically dis-connect your Windows Hard Drive and install Linux on your second HDD. In order for this to work, your BIOS has to have a Setting to allow you to change the Boot Order of your Drives. In this Fashion both Operating Systems are completely independent of each other. You would change to Boot Order in your BIOS every Time you wanted to boot the other OS.

Should you ever decide to upgrade Windows, it won affect Linux and you won´t have to disconnect the Drive providing the Windows Drive is selected in the BIOS. If you however wish to upgrade Linux at some future Point, you will have to again physically dis-connect the Windows Drive.

---

### Post by ssican on 2009-04-12
There is a Guide for DUALBOOT TWO HARD DRIVES:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

Also, there is an HOW-TO MULTI BOOT LINUX on the FULL CIRCLE MAGAZINE, issue #8-December 2007, pages 13-14-15:
[http://fullcirclemagazine.org/issue-8/](http://fullcirclemagazine.org/issue-8/)

This HOW-TO, was written by linuxloop.com:
Setting up a dual- or multi- boot Linux system:
[http://www.linuxloop.com/dualboot/index.shtml](http://www.linuxloop.com/dualboot/index.shtml)

EDIT 1
On the Home Page "ILLUSTRATED DUAL BOOT SITE":
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
THERE ARE LINKS for **three different Ubuntu 'Desktop CD' graphical installations**:

1 - Hardy Heron LTS/Windows XP Dual Boot - **Graphical Installation A**:
[http://mywebsite.bigpond.net.au/dfelderh/p24.html](http://mywebsite.bigpond.net.au/dfelderh/p24.html)

2 - Jaunty Jackalope / Windows7 Dual Boot or Multi Boot - **Graphical Installation B**:
[http://mywebsite.bigpond.net.au/dfelderh/p23.html](http://mywebsite.bigpond.net.au/dfelderh/p23.html)

3 - Jaunty Jackalope/Windows 7 Dual Boot or Multi Boot - **Graphical Installation C**:
[http://mywebsite.bigpond.net.au/dfelderh/p22.html](http://mywebsite.bigpond.net.au/dfelderh/p22.html) 

EDIT 2
Another Guide, of Ubuntu Documentation > Community Documentation:
**How To Dual-Boot Ubuntu and Xp after Installing Them Separately on Two HDs**:
[https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs](https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs)

---

### Post by richlyn9 on 2009-04-22
Great!!
so this is pretty simple ..just follow the installation wizard choosing the correct drives and its done.

just need to clear one doubt :
Will i need to create a swap partition on the drive that ubuntu will be installed?

---

### Post by Partyboi2 on 2009-04-22
You should be able to choose "guided use entire disk" then select the hard drive you want to install ubuntu on and it should automatically setup a / and a /swap for you.

---

