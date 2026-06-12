---
title: "Dual Booting XP and Ubuntu on Separate HDD Help?"
date: 2009-01-12
forum: Installation &amp; Upgrades
---

### Post by bhoemen on 2009-01-12
I have ubuntu installed and recently installed xp on another harddrive and no it just boots into xp, how do i get the option of booting into either?

---

### Post by Pumalite on 2009-01-12
Reinstall Grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
You might have to change the boot order of your hard drives
You might have to edit menu.lst to include XP
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

---

### Post by caljohnsmith on 2009-01-12
In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---

