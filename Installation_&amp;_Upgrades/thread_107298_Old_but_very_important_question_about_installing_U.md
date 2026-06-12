---
title: "Old but very important question about installing Ubuntu on a partition"
date: 2005-12-22
forum: Installation &amp; Upgrades
---

### Post by anshumanoz on 2005-12-22
I guess you hear this question many times but here it goes..(sorry if this question has been answered before many times over)

I have a windows XP installation on my laptop and I have a brand new external 200 GB hard drive. I want to partition a part of the external hard - drive and install ubuntu on it. I also want to have the choice of booting with windows xp or ubuntu when my computer starts up. I have already downloaded ubuntu but now I don't know what to do next.

Any help will be greatly appreciated as I've always been a Microsoft user and have never used linux before.

Thanks in advance :)

---

### Post by matthew on 2005-12-22
[https://wiki.ubuntu.com/WindowsDualBootHowTo](https://wiki.ubuntu.com/WindowsDualBootHowTo)

This link should be helpful to you.

---

### Post by landotter on 2005-12-22
As long as the drive gets recognized by Ubuntu, any general thread on installation and dual booting should serve you fine.

Ubuntu will install the GRUB bootloader on your master boot partition on the lappy's hard drive, which will give you a screen offering XP or Ubuntu upon boot.

Just make sure to choose the correct drive when running the install-[COLOR=Red]-do NOT choose hda1[COLOR=Black]--as that will be the HDD that's already in the laptop, your usb drive will probably be called "sda" or similar.[/COLOR][/COLOR]

---

