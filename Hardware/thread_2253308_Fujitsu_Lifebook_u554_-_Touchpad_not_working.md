---
title: "Fujitsu Lifebook u554 - Touchpad not working"
date: 2014-11-18
forum: Hardware
---

### Post by BenRbtz on 2014-11-18
A noob to Linux so handle me with care :-P I have a Fujitsu Lifebook u554 which I decided to put a copy of Ubuntu 14.10. During and after installing the copy of ubuntu the touchpad did not function at all but a mouse worked flawlessly. What would be the course of action to be taken to resolve the problem? Sorry if the is not enough information, not too sure what other information is need.

Any help will be highly appreciated!

---

### Post by mauro11 on 2015-01-26
As stated here [https://wiki.debian.org/InstallingDebianOn/Fujitsu/LifebookU554/jessie](https://wiki.debian.org/InstallingDebianOn/Fujitsu/LifebookU554/jessie)
For your pc is needed some configuration to activate touchpad.

You must follow these steps

open a terminal and write this and insert your password:
[FONT=courier new]
  sudo nano /etc/default/grub[/FONT]

in nano find the line:

[FONT=courier new]  GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"[/FONT]

edit it with:

[FONT=courier new]  GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.notimeout"[/FONT]

save it (CTRL+O and then ENTER)

exit from nano (CTRL+X)

back in terminal type:

[FONT=courier new]  sudo update-grub[/FONT]

restart your ubuntu.

Sorry for my poor english

---

