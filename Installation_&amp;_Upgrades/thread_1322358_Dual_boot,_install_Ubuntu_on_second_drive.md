---
title: "Dual boot, install Ubuntu on second drive?"
date: 2009-11-10
forum: Installation &amp; Upgrades
---

### Post by JoeBlotnik on 2009-11-10
I want to learn about UBUNTU but have some basic questions about installing it.

I want to install a 2nd HD (drive D) on a WinXP machine, install a dual boot on that PC and have it boot to the Ubuntu installed on the drive D by itself.

Can this be done using the Windows Wubi installer, using the original downloaded "ubuntu-9.10-desktop-i386.iso" file?

Believe I've read somewhere that by using the Win Wubi installer I can uninstall Ubuntu by using the Add & Remove Software in XP's control panel if I need to. Did  I understand this correctly?

I would prefer to run Ubuntu on a USB Flash Drive but cannot get the Live CD to format the USB Drive, so want to try it this way....

Thanks for any help.

---

### Post by dhavalbbhatt on 2009-11-10
The best way for you to try Ubuntu will be to use a LiveCD. You don't need to install Ubuntu anywhere on your computer - you can run it directly from your computer's CD drive. Having said that, you can install Ubuntu a couple different ways. If you want to install it on a hard drive, then you will have to burn an ISO image onto a CD and install Ubuntu from the CD - directly onto the hard drive. During the installation process, GRUB will be installed, allowing you to dual boot - essentially giving you the capability to either boot into Ubuntu or Windows. If you don't want that option, then you can install into Windows as just another program (you can then remove Ubuntu using add/remove programs, if you don't like it).

---

### Post by oldfred on 2009-11-11
If you are adding a new hard drive my recommendation is to install Ubuntu just to the new hard drive. Normally that install would add grub to the MBR of the windows install so you can boot windows, but you have to reinstall windows boot loader if you uninstall Ubuntu.

If in BIOS you make the new drive first, boot from the liveCD and install Ubuntu will be 100% on the new drive, windows on the second drive and Ubuntu will map windows to think it is first so it will run. Then if you do not want Ubuntu you can change the boot order in BIOS so windows is frist, it will still boot since its boot loader is still in that drive's MBR. You then could erase/reformat the Ubuntu drive.:(

---

