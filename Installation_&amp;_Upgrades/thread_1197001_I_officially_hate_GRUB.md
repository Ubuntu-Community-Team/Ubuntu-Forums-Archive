---
title: "I officially hate GRUB"
date: 2009-06-25
forum: Installation &amp; Upgrades
---

### Post by joshh88 on 2009-06-25
So I tried PCLinuxOS and liked it so I added it to a new partition after starting it up I can't get Ubuntu to load it says it can not find Ubuntu. I can't figure out how to edit grub in pclinuxos and honestly the live cd was way faster so I want to delete it and go back to Ubuntu

had to edit said PCLinuxOS instead of Ubuntu

---

### Post by Therion on 2009-06-25
So put the PCLOS LiveCD back in the drive, boot from it and install using the whole drive.  

Problem solved.

---

### Post by presence1960 on 2009-06-25
if you are going to reinstall PCLinux OS, then install it to the same partition and install it's grub to partition rather than MBR. Then Boot Ubuntu Live CD and restore it's GRUB to MBR. Then finally edit Ubuntu's menu.lst to chainload PCLinux OS just as you would chainload Windows. When you boot you should get Ubuntu's GRUB since it is in MBR, when you then choose the chainloaded PCLinux option in GRUB menu it will pass it off to PCLinuxOS's GRUB in it's partition and you can then choose which kernel to boot into PCLinux OS.

Example: 
> title         PC Linux OS
rootnoverify  (hdx,y)
chainload     +1

---

