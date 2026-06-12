---
title: "Upgrade from 8.04 to 8.10 boot menu gone"
date: 2009-01-14
forum: Installation &amp; Upgrades
---

### Post by geraniu on 2009-01-14
I recently upgraded from 8.04 LTS to 8.10.  Everything went ok until it restarted my computer.. I run a dual boot with Vista (i know, evil me).  My vista worked fine before, and I can still access the vista system, no problem...But the menu option for all the previous ubuntu versions including 8.04 and 8.10 are gone, except for the ubuntu memtest function... How do I get access to my Ubuntu 8.10 back?  Any ideas?  Thanks.

---

### Post by frost151n on 2009-01-15
Do you know whether your bootloader is GRUB or Win MBR???
If it's GRUB boot the Live CD, attach the file /boot/grub/menu.lst (Note: that's a small 'L' not the No. 1)

--x--
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by kranny on 2009-01-15
Are you sure the entry **"#howmany=all"** in  menu.lst is the same or changed to **"#howmany=0&#8243;**
Btw run run "sudo update-grub" to update changes

---

### Post by caljohnsmith on 2009-01-15
How about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your booting problem might be.

---

