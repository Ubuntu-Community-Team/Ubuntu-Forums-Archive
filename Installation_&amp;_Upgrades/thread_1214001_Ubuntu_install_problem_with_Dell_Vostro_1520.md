---
title: "Ubuntu install problem with Dell Vostro 1520"
date: 2009-07-15
forum: Installation &amp; Upgrades
---

### Post by x53x6ex69x67x67x65x72 on 2009-07-15
Hi all
I'm trying to install Hardy on my Dell Vostro 1520
But while booting with Live CD for install I get this error:
```
udevd-event[1400] : run_program :'/sbin/modprobe' abnormal exit

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Build-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)
```
I found that its because of Network adaptor and when I disabled "Integrated NIC" from BIOS , Live CD has been booted without problem!!!!
Knoppix boots but it ignores network interface and lspci says my network adaptor is:
```
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
```
Now, I need My network adaptor ! I can Install Ubuntu with this trick but when I enable it again Ubuntu will not boot again , 
What can I do?
Can I disable it - install ubuntu and install it's driver from source then reEnable it ?
does it work?
does anyone tried it?

Thank you.

---

