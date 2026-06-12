---
title: "Dual boot partition problem"
date: 2009-01-17
forum: Installation &amp; Upgrades
---

### Post by Sonofsurak on 2009-01-17
I am a total and complete noob to Ubuntu.  I'm sick and tired of Microsoft and being practically forced to use their crappy software.  That being said, I was intrigued by Ubuntu and decided to try it.  Everything installed without a hitch except that my machine isn't dual booting.  I can go into Computer Management (through XP) and I can see the partition that Ubuntu created.  It tells me that it is a healthy but unknown partition.  I don't have the option to make it an active partition.  Does anyone have any idea how to fix this?  I'm looking forward to playing with Ubuntu.  I'm hoping I can get rid of Bill Gates altogether.

---

### Post by taurus on 2009-01-17
Did you install Ubuntu on it own partition or did you use wubi?

---

### Post by caljohnsmith on 2009-01-17
In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your booting problem might be.

---

