---
title: "Installing Ubuntu and Win7 on seperate drives"
date: 2009-10-13
forum: Installation &amp; Upgrades
---

### Post by ChasHutch on 2009-10-13
Hey all,

I have recently purchased a second 320g drive for my pc and would like the choice of booting to windows or ubuntu and need some clarification.

When I put the second drive in and put windows on it, what OS will boot by default?

The two OS's don't need to know about each other as all files are stored on the server.

Thoughts?

Thanks,
Hutch

---

### Post by skatinjj on 2009-10-13
You would have to look in BIOS and see which drive is booting first.  If it is the drive with Ubuntu, then Ubuntu.  If it is the drive with Windows, then Windows.

---

### Post by ChasHutch on 2009-10-13
I guess my real question is, how do I select between the two at boot time?

Thanks,

---

### Post by skatinjj on 2009-10-13
If Ubuntu is booting first you have to configure grub (assuming you are using grub) first.
Add this to your /etc/grub/grub.conf:

title Windows
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

If you want Windows booting first then reply back stating that and I will provide those instructions.

---

### Post by ChasHutch on 2009-10-13
I want to boot to Ubuntu and will use your instructions.

Thank you for your quick response.

---

### Post by skatinjj on 2009-10-13
Not a problem at all.  Post back and let me know what happens.

---

### Post by presence1960 on 2009-10-13
> **ChasHutch said:**
> I guess my real question is, how do I select between the two at boot time?

Thanks,

Then you want the disk with Ubuntu (which has GRUB on it) booting first in BIOS.

First you want to install windows. Before doing so set the 320 GB disk that you will put windows onto as first hard disk to boot in BIOS. Boot the windows install CD/DVD and install windows.

When complete reboot, go back into BIOS and set the other disk with Ubuntu on it as first hard disk to boot in BIOS. This will bring up GRUB. Boot into Ubuntu and then edit your menu.lst file to add the windows entry so you have the choice of Ubuntu or Windows at the GRUB menu. If you don't know how to do this post back.

---

### Post by presence1960 on 2009-10-13
> **skatinjj said:**
> If Ubuntu is booting first you have to configure grub (assuming you are using grub) first.
**_Add this to your /etc/grub/grub.conf:_**

title Windows
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

If you want Windows booting first then reply back stating that and I will provide those instructions.

Unless he is using 9.10 I don't think he is using GRUB 2. grub.conf is a GRUB 2 file. The file to edit for Legacy GRUB is menu.lst located here: /boot/grub/menu.lst

---

### Post by QIII on 2009-10-13
Just wanted to say "Nice Boxer".

We've always had a Boxer or two in the house since we got married a while ago...

---

### Post by darco on 2009-10-13
I recently partitioned a 2nd hdd and added Karmic which uses Grub2. The first hdd has Mint 7 and Win 7.
I first disconnected the first hdd, installed Karmic on the 2nd hdd. After boot up,Grub2 picked up Mint7 and Win7 after I re-connected the first hdd. Then I logged into Mint and grub2 picked up the 2nd hdd. Very nice!

darco

---

