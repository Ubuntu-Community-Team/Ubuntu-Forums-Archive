---
title: "ubuntu"
date: 2009-05-05
forum: Installation &amp; Upgrades
---

### Post by r.felker on 2009-05-05
will not boot all it goes to is a command prompt need help please
my computer is an Intel core2 duo e7200 asus p5q se plus 4 GB crucial xfx 8600gs
SEAGATE 1TB Barracuda 7200.11 SATA II w/ NCQ, 32MB Cache

---

### Post by ptn107 on 2009-05-05
Does it go to a GRUB prompt (grub>) or terminal prompt (user@host:$)?

---

### Post by r.felker on 2009-05-05
grub

---

### Post by caljohnsmith on 2009-05-05
In order to get a clearer picture of your setup related to your booting problem, how about booting your Ubuntu Live CD (the Ubuntu install CD), download the **Boot Info Script** to the Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

