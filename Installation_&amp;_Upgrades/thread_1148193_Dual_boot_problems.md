---
title: "Dual boot problems"
date: 2009-05-04
forum: Installation &amp; Upgrades
---

### Post by raven128 on 2009-05-04
i had installed on my computer vista sp1. when i decide to install ubuntu, i bought another harddrive solely for ubuntu purposes. on appropriate installation step i set grub installation on ubuntu hdd, not on vista. installation goes fine, but my vista don't starts anymore. it said - "bootmgr is missing". i've tried to use repair mode through vista install - it finds my vista installation but cant save bcd information - bootrec.exe just cant find where to save it. anyone knows how can i get my vista back without reinstalling it?

---

### Post by Sef on 2009-05-04
Set Vista as the boot from with [Super GRUB Disk]("http://supergrubdisk.org/").

---

### Post by caljohnsmith on 2009-05-04
I think it would help to first get a clearer picture of your setup, so how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your Vista booting problem might be.

---

