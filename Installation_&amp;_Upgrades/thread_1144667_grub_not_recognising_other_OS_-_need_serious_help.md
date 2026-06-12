---
title: "grub not recognising other OS - need serious help"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by robbo130 on 2009-04-30
hey

i'm new to ubuntu - installed on an external hard drive the other day, is running fine ( on it at the moment =])

problem im having is: laptop came with XP. i added fedora to it on the same harddrive. I could swap between the two using fedora's boot manager. but now, grub refuses to accept fedora. im pretty sure ive gotten the menu.lst file ok, but heres the relevant info: 

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Microsoft Windows XP Home Edition
root        (hd0,1)
savedefault
makeactive
chainloader    +1

# This entry is a guess. Fedora Core 10, kernel 56
# possibly on /dev/sda3
title        Fedora Core 10, kernel 56
root        (hd0,3)
kernel        /boot/vmlinuz-2.6.27.21-170.2.56.fc10.i686
initrd        /boot/initrd-2.6.27.21-170.2.56.fc10.i686.img
savedefault
makeactive
chainloader    +1

as you can see, XP has hd0,1 due to there being the recovery partition before it (hd0,0).
and when i try to boot fedora through grub, it says that the partition cannot be mounted. 

any suggestions?

cheers in advance guys

Xavier

---

### Post by meierfra. on 2009-05-01
Please don't start multiple threads on the same subject.
And please let people know that your problem has been solved.

[http://ubuntuforums.org/showthread.php?t=1144979](http://ubuntuforums.org/showthread.php?t=1144979)

---

