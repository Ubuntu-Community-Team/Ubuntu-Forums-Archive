---
title: "Getting Files From USB NTFS Hard Drive"
date: 2006-09-12
forum: Hardware &amp; Laptops
---

### Post by rcplain123 on 2006-09-12
I have recently switched from Windows to Ubuntu on my laptop. My desktop is still running Windows. I took the IDE hard drive out of my desktop and put it in an adaptec USB enclosure in hopes of getting my music off there. Unfortunately I have not been able to figure out how to get to my USB hard drive. It does not show up in Places. Please help!!!

---

### Post by Thirsteh on 2006-09-12
Type 'tail -f /var/logs/dmesg' in a console, and see if it says it has found a device when you plug in the USB drive.. It might even tell you what's wrong, if there is anything wrong - perhaps a kernel module that couldn't be probed.

---

### Post by Valhalla on 2006-09-12
Please plug in your harddrive, open the terminal application and type sudo fdisk -l

Then paste the output here.

---

