---
title: "Grub menu after second distro"
date: 2008-10-03
forum: General Help
---

### Post by Arcnsparc on 2008-10-03
So I added Debian, because I figured I should start using it if I was enjoying Ubuntu so much.  Debian is on it's own partition

/dev/sda1  Swap
/dev/sda2  /home
/dev/sda3  Debian /root
/dev/sda4   *   Ubuntu /root & booting partition


So... for some reason, the Grub menu being used is in the /boot folder of sda3 there instead of sda4 where I thought it would come from...  I want to install a different distro to try out on sda3 so before that i need to change Grub menu to use the sda4/root/boot/grub/menu.list instead of the sda3 one....  Any ideas?

Thanks

---

### Post by fsmithred on 2008-10-05
Boot into ubuntu, and run 'sudo grub-install /dev/sda'. 

Next time, tell your second distro not to install grub, and you can just add a section to your existing menu.lst for the new distro.

---

