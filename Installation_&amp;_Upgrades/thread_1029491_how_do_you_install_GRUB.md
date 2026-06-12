---
title: "how do you install GRUB?"
date: 2009-01-03
forum: Installation &amp; Upgrades
---

### Post by dcjose20 on 2009-01-03
i just installed ubuntu 8.10 on a 2nd hdd i had. When i turn my computer on it doesnt give me the choice of which hdd to boot from. It will just boot windows vista. Does anybody know how to fix this. I have downloaded super grub disk but im not sure how to exactly use it.

---

### Post by openn0de on 2009-01-03
Have you set the computer to boot from the 2nd Hard Drive in the BIOS? Im not sure if this will completely fix your problem but that would be my guess. To get into the BIOS you usually have to press the button it states when the computer first boots, usually F2, F12, or Delete.

---

### Post by dcjose20 on 2009-01-03
i know that is one way, but i dont want to automatically boot in ubuntu cause other people sometimes use the computer so that is why i want it to ask me which operating system to load.

Edit: You are correct, my apologizes.

---

### Post by caljohnsmith on 2009-01-03
If you can set your computer BIOS to boot the Ubuntu drive, you could add an entry in the Grub menu to boot Vista on the other drive. If you would like a little help doing that, how about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it.

If you don't have internet connectivity when using the Live CD, you can instead right-click [this link]("http://home.comcast.net/~ubuntu_grub/boot_info_script.txt") to the script in your web browser, choose "Save link as...", save the "boot_info_script.txt" file, transfer it to your Ubuntu desktop on the Live CD via USB stick, floppy, or however you want to do it, and then do the following in a terminal:
```
sudo bash ~/Desktop/boot_info_script.txt
```
The results of that script will help clarify your setup.

---

