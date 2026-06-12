---
title: "dell utility partition+grub/pc+syslinux boot anyone"
date: 2009-10-28
forum: Installation &amp; Upgrades
---

### Post by ghat on 2009-10-28
hi

I tried doing this without sucess, but wanted to know if any advanced users have had success with this... 

1. unbox a dell an install the default OEM OS (in my case XP)
/dev/sda1 => dell system utility
/dev/sda2 => XP
2. use systemrescue CD to resize and reshuffle disk data with gparted
end up with
/dev/sda1 => Linux
/dev/sda2 => Windows XP
dell_utility.dd => using dd if=/dev/sda1 of=dell_utility.dd
3. Install ubuntu on /dev/sda1 setup dual boot.. 
4. Ubuntu and Windows dual book work...
5. install syslinux in ubuntu and try to add grub option to load 
dell_utility.dd (image) using syslinux

Did not work for me... has anyone tried going this way ?

Ghat

---

