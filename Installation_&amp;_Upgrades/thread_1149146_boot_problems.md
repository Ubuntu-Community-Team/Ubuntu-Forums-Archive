---
title: "boot problems"
date: 2009-05-04
forum: Installation &amp; Upgrades
---

### Post by wclarowe on 2009-05-04
I recently upgraded to Ubuntu 9.04 on a system that is on the same IDE drive with windows XP (ugh).  I also have 2 other hard drives one with 9.04 and one with 8.10.  When I try to boot I have different results depending on the boot order of the drives.  With the IDE drive first the only drives presented on boot is the IDE drive and bothe systems boot.  If either of the SATA drives are set to boot first neither of the systems on the IDE drive will boot, nor will the other SATA drive boot.  Before updating everything was fine.  Any suggestions?

---

### Post by Mark Phelps on 2009-05-05
My guess is that you have an MBR on each drive -- which, when that is the boot drive, will then determine which OS(s) boot.  

If you were booting into Ubuntu before and using GRUB to select your OS, when you upgraded to 9.04, it overwrote the menu.lst file.

I also found that when I updated to 9.04, it changed the order of my hard drives such that "sda" was now "sdc".  This played havoc with my menu.lst file such that I had to do a lot of hand-editing to get it to work again.

You'll need to do the following:
1) Set up the boot to the drive you want
2) If that drive won't boot into Ubuntu, use a LiveCD to boot.
3) Do an "sudo fdisk -lu" (that's a lowercase L, not a one), and a "sudo blkid" to get partition and UUID information.
4) Find the menu.lst file that is being used for boot.  You might have to run GRUB and do a find /boot/grub/stage1 to locate the directory and drive.
5) Using the fdisk and blkid info, hand-edit the menu.lst file to get it to boot to the proper drives and partitions for each stanza.

---

### Post by Bartender on 2009-05-05
> **wclarowe said:**
> Before updating everything was fine.  Any suggestions?
Did the update include a kernel update?  I tried multi-booting Linux OS'es and gave up because of the headaches involved every time there was a kernel update.  
Unless you go in and manually edit out the UUID's in - oh, crap, is it fstab? - I think so, anyway, there are some tricks to this.  It's NOT as easy as dual-booting Windows and Ubuntu.  
My suggestion - just stick with the latest Ubuntu.  I think you'd find you're not using the other versions anyways even after the hassle of setting them up correctly.

---

### Post by caljohnsmith on 2009-05-05
If you would like specific help with how to get your multiple HDD boot setup to work in the best way possible, how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

John

---

