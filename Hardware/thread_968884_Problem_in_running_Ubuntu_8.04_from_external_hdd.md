---
title: "Problem in running Ubuntu 8.04 from external hdd"
date: 2008-11-03
forum: Hardware
---

### Post by bilol on 2008-11-03
Hi friends,
I have installed Ubuntu 8.04 in an external hdd through my desktop. When I try to run the OS in some other desktop using that external hdd it is giving “Grub Loading error”
What shall I do?Please suggest.
Thanks in advance

---

### Post by pansz on 2008-11-03
press ESC to enter the Grub menu

in the Grub menu, press 'e', then see the line with root (hd1,0) or alike. 

change (hd1,0) to (hd0,0), then press 'b' to boot.

try that, if you can boot with (hd0,x), then you can edit /boot/grub/menu.lst to save your change permanately.

---

### Post by bilol on 2008-11-05
Hi,
**Yehhh...Solved at last.**.
From ubuntu menu I pressed 'e' to enter edit mode then changed "sda4" to "sdb4" and pressed "b" to boot. Then I went to CUI mode of ubuntu with the error:"Failed to start the Xserver". Next I followed  Xorg's 9:58 pm. post of [this]("http://ubuntuforums.org/archive/index.php/t-116902.html")and...when I lost all my hopes all on a sudden (after the "startx" command) the ubuntu screen appeared.
Thanks a lot for your advice that helped me too.

---

