---
title: "Removing Ubuntu"
date: 2008-10-13
forum: General Help
---

### Post by LegendFury on 2008-10-13
How do I completely uninstall Ubuntu and make my hard drive completely empty. Thanks.

---

### Post by shawnrgr on 2008-10-13
Format it.

What OS will you be using? Its its your only partition then just install Windows or whatever you plan on using over top, it will format the disk for you. 

if you want it to just be for storage, load up an ubuntu live cd and user gparted to format the drive in any fs you choose.

---

### Post by LegendFury on 2008-10-13
I have sort of a problem though. I recently upgraded my mobo, ram, and cpu. But I had a old IDE dvd drive, so I have to use a IDE to PCI card. So I don't think my DVD drive gets read at startup/boot menu.

Also, how do I format Ubuntu?

Thanks for the help.

---

### Post by bodhi.zazen on 2008-10-13
> **LegendFury said:**
> How do I completely uninstall Ubuntu and make my hard drive completely empty. Thanks.

[DBAN](http://www.dban.org/)

But none of that is really necessary, just proceed with installing Ubuntu and either re-partition with gparted or use the entire disk.

---

### Post by LegendFury on 2008-10-14
> **bodhi.zazen said:**
> [DBAN](http://www.dban.org/)

But none of that is really necessary, just proceed with installing Ubuntu and either re-partition with gparted or use the entire disk.

If I do that, will I be able to re-install Windows XP on a USB drive?

---

### Post by bodhi.zazen on 2008-10-14
> **LegendFury said:**
> If I do that, will I be able to re-install Windows XP on a USB drive?

Sure, why not ? DBAN merely wipes the HD (I have DBAN and reinstalled windows in the past for virus infected systems).

---

### Post by LegendFury on 2008-10-15
> **bodhi.zazen said:**
> Sure, why not ? DBAN merely wipes the HD (I have DBAN and reinstalled windows in the past for virus infected systems).

Well, to answer the why not, it's because if I try to reinstall windows on my ubuntu system it says, "failed to load kernel image: linux". So I figured maybe if I wiped ubuntu first, I could load WinXP from my USB without any problems.

---

### Post by SunnyRabbiera on 2008-10-15
well instead of just hopping back onto windows can you tell us about the issues you had with ubuntu?
We are a community of helpers you know :D

---

### Post by Archmage on 2008-10-15
> **LegendFury said:**
> Well, to answer the why not, it's because if I try to reinstall windows on my ubuntu system it says, "failed to load kernel image: linux". So I figured maybe if I wiped ubuntu first, I could load WinXP from my USB without any problems.

You need to change the boot sequence in your BIOS. Without it even booting with an empty harddrive will fail.

---

### Post by LegendFury on 2008-10-15
> **Archmage said:**
> You need to change the boot sequence in your BIOS. Without it even booting with an empty harddrive will fail.

Can't you just press F10 (or w/e it is) at startup to enter boot menu, then you can boot from USB drive?

---

### Post by LegendFury on 2008-10-16
Bump

---

### Post by louieb on 2008-10-16
> **LegendFury said:**
> Can't you just press F10 (or w/e it is) at startup to enter boot menu, then you can boot from USB drive?

Maybe, between me the wife and kids we have 3 desktops and 3 laptops, No two change the boot device the same way.  There may be message at startup saying press <whatever key to> change boot device or press <what ever key to> enter setup. If you don't get a message you'll  just have to go the manufactures website to find out how to change the boot device. 

Good Luck.

---

### Post by shawnrgr on 2008-10-17
I believe boot from usb might need to be enabled in bios... not sure on that one though. Also your usb key needs to be formated and made bootable, if you haven't already done that.

---

