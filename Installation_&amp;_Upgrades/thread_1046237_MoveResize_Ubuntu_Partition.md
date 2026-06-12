---
title: "Move/Resize Ubuntu Partition"
date: 2009-01-21
forum: Installation &amp; Upgrades
---

### Post by paulc86 on 2009-01-21
Hi everyone,

Could any one offer advice on moving my installation to another partition or even just resizing it.

Currently ubuntu is on the first partition, I need to make a little bit of space to install XP unfortunately. I did have XP installed on a 3rd partition but I cant get it to boot now.

Any advice on what I would need to update and how to do this such as the fstab file, etc would be appreciated.

Thanks

P

---

### Post by caljohnsmith on 2009-01-21
Just out of curiosity, what exactly happens when you try to boot XP, and what do you think led up to the problem? I'm just wondering because it may be that your XP install is actually salvageable, and you may not need to change your partitions and reinstall. In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and maybe shed some light on your Windows booting problem.

---

