---
title: "Help - Cannot Boot"
date: 2008-09-14
forum: General Help
---

### Post by mistahchen on 2008-09-14
I have two hard drives - I have Windows XP installed on one, and I had Ubuntu installed on the other. I reformatted the second one (the one on which Ubuntu was installed) from within Windows XP, and once I restarted, my computer won't boot into Windows at all. It gives me a GRUB 17 error. I need to be able to boot into Windows, and any help would be greatly appreciated.

I booted Ubuntu off of the CD (which luckily I had) and that's how I'm on right now.. so I can boot from CD / Flash drives, I just can't boot Windows.

Thanks in advance!

---

### Post by cyclobs on 2008-09-14
try this thread

[http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)

---

### Post by confused57 on 2008-09-14
Boot into Ubuntu, open a terminal(Applications---Accessories---Terminal), post the output of:
```
sudo fdisk -l
```
-l is a small "L"
and
```
gedit /boot/grub/menu.lst
```
menu.lst is short for menu.list
(you can probably just post the Ubuntu & Windows boot entries)

Someone should be able to help you with this info posted.

---

