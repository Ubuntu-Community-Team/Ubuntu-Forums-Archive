---
title: "BOOTMGR missing"
date: 2009-07-13
forum: Installation &amp; Upgrades
---

### Post by VonTenko on 2009-07-13
I'm trying to install the latest version of Ubuntu onto a computer, but when I try to install it from the CD I burned, it says that BOOTMGR is missing and to press "crtl+alt+delete" to restart it. If I restart it, I get the same problem. 

I searched the forum and it seems all the issues related to BOOTMGR are with dual boots. I am trying to run Ubuntu as the only OS on the computer. 

Any ideas of how to fix this?

---

### Post by Vakman on 2009-07-13
Was Windows previously on this machine? Whether it was or wasn't you should reinstall GRUB boot menu. Follow this: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
That link will show you how to install the GRUB boot menu from the Ubuntu Live CD.

---

### Post by VonTenko on 2009-07-13
ThisIsLaw, thank you replying. My issue is though that the computer won't boot the CD at all. So I can't install GRUB. It repeatedly tells me to restart the computer. 

Any other suggestions? or am I doing something wrong?

---

### Post by Vakman on 2009-07-13
> **Thisislaw said:**
> 
That link will show you how to install the GRUB boot menu from the Ubuntu Live CD.
Yes, this will show you how to install GRUB from the Live CD of Ubuntu so that you do not need to reinstall. Just boot from the CD you originally used to install Ubuntu.

---

### Post by ronparent on 2009-07-13
VonTenko

In it possible that you merely copied the iso to your cd. In such a case you wouldn't be able to boot from the cd - ie no boot manager. You need to use one of the many programs that burns the iso image to the cd. The operative action is to find a menu option that permits you to "burn image". What cd burning software are you using ?

---

### Post by Vakman on 2009-07-13
I thought he was saying he installed Ubuntu and he can't boot from it. And you can always boot from the CD since you can just choose to boot from CD before hard disk. Just because there is not boot manager does not mean you can't boot from the CD since the boot manager is on the hard drive anyway.
I guess I was reading incorrectly.

---

### Post by VonTenko on 2009-07-13
ronparent, I used NTI Media Maker 8. It should have burned it properly I believe. I could try to use PowerISO, I have it at my disposal. 

Thisislaw, I have not installed Ubuntu. It won't load the CD.

---

### Post by merlinus on 2009-07-13
When you look at the contents of the cd in windows, it should show folders and files, not simply one large .iso file.

Also, you might perform a checksum on your .iso, and make sure you burn it as a disk image (not a data disk) at no more than 4x.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

