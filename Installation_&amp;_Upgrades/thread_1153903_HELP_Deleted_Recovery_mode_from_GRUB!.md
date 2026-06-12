---
title: "HELP: Deleted Recovery mode from GRUB!"
date: 2009-05-09
forum: Installation &amp; Upgrades
---

### Post by shark1997 on 2009-05-09
**[FONT="Arial Black"][SIZE="7"]How do i get recovery mode back?[/SIZE][/FONT]**

---

### Post by caljohnsmith on 2009-05-09
Shark1997, please do not use such a large, bold font to ask your question, because it is considerend "yelling". It would help if you would give some information and details about your problem rather than simply demanding "How do i get recovery mode back?". If you want help, how about downloading the **Boot Info Script** to your Ubuntu desktop (can be the Live CD):

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

John

---

### Post by lswb on 2009-05-09
Depending on what you did to delete it, it may be as simple as typing this in a terminal:

sudo update-grub

---

