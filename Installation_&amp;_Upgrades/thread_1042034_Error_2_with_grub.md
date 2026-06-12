---
title: "Error 2 with grub"
date: 2009-01-17
forum: Installation &amp; Upgrades
---

### Post by kaar3l on 2009-01-17
Hello

I have a problem with booting to ubuntu.
My partition table was like that before

Vista
XP
Mac
extended
   linux /
   home
   swap

Now i changed it a bit and reinstalled xp then installed grub to mbr with super grub disk.

XP
extended
   linux /
   home
   swap

Has anybody any thoughts how to solve this, i have been trying to resolve it for last day. :(

Any help appriciated >(

---

### Post by caljohnsmith on 2009-01-17
In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your booting problem might be.

---

