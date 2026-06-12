---
title: "Can't keep touchpad working"
date: 2012-03-01
forum: Hardware
---

### Post by Denco1 on 2012-03-01
Hey all. I have this weird problem with touchpad on my Toshiba Satellite L650-1K6 laptop. Everytime I start OS (Xubuntu 11.10 64bit) touchpad works. But after an unknown time, it stops working. I can see *Unavailable touchpad* in Jupiter. Any ideas, how to keep touchpad working? Xubuntu is in dualboot with Windows 7 64bit.
Thanks for all replies.

---

### Post by Denco1 on 2012-03-04
Anyone?

---

### Post by HunterDX77M on 2012-03-04
Maybe you'll find something useful here. I've got the same problem.

[http://ubuntuforums.org/showthread.php?t=1915057]("http://ubuntuforums.org/showthread.php?t=1915057")

---

### Post by Denco1 on 2012-03-04
Thanks, I will check it and report results.

---

### Post by Denco1 on 2012-03-05
Did not find anything helpfull. Btw, my problem have happened now again. Touchpad worked 10 minutes ago. Now it is not working.

---

### Post by Denco1 on 2012-03-13
It seems, that I found a solution. I used a command **dmesg** and got an error: TouchPad at isa0060/serio1/input0 lost sync at byte 1. So I looked for this error on Google and found a solution, that seems working (still in testing):
(1) Terminal - sudo gedit /boot/default/grub
(2) Found a line GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
(3) At the on of that line add i8042.nomux=1
(4) So after edit, line looks like this: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.nomux=1"
(5) Save the file

Touchpad has been working for 3 hours right now. I can turn it on / off everytime a I want. Hope it helps.

---

### Post by fallenstar on 2012-03-13
I'm having problems on a sony vaio e series; touchpad is erratic at best, unusable. When I edit the grub conf file, I get when I save it:

(gedit:3462): Gtk-WARNING **: Attempting to store changes into '/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.9PH3AW': No such file or directory

come up in terminal. Any ideas?

---

### Post by fallenstar on 2012-03-13
Ignore me, it's started working now! Restarted twice, and disabled scrolling, as well as the fix above.

---

