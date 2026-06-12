---
title: "Screen Brightness"
date: 2008-05-15
forum: Hardware
---

### Post by Recruit0 on 2008-05-15
I'm mostly new to Linux (finished a basic training Unix course just recently). I installed Xubuntu on my Gateway M-6846. Hardware specs can be found at:

[http://support.gateway.com/s/Mobile/2008/Avalon/1015342R/1015342Rsp2.shtml](http://support.gateway.com/s/Mobile/2008/Avalon/1015342R/1015342Rsp2.shtml)

How do I adjust the screen brightness? I've searched around and most seem to be brand specific solutions. I have a keyboard combo (Fn + Down Arrow/Up Arrow) that is supposed to adjust the brightness but it doesn't do anything. It just shows a bar inc/decreasing.

---

### Post by morgengenuss on 2008-05-16
have you tried [this?]("http://ubuntuforums.org/showthread.php?t=794362")

---

### Post by Recruit0 on 2008-05-16
None of that works. There is no "System > Preferences > Power Management" and it says "Permission denied" even if I use sudo with those commands that  badfish591 suggested. I'd try upgrading to 8.10 but AFIAK it isn't even out yet.

EDIT: Tried the commands with:

sudo bash
cd /proc/acpi/video/VGA/LCD/
nano brightness

Tried editing the file. Apparently can't be changed (even though I saved to it in nano).

---

