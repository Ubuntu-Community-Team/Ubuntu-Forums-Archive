---
title: "installed windows effed up grub"
date: 2006-01-07
forum: Installation &amp; Upgrades
---

### Post by Akya on 2006-01-07
i installed windows on a seperate hard drive then linux but now when i try to boot linux i just get grub error 17 with both hard drives in and error 21 with only linux pluged in

---

### Post by codejunkie on 2006-01-07
[QUOTE=Akya]i installed windows on a seperate hard drive then linux but now when i try to boot linux i just get grub error 17 with both hard drives in and error 21 with only linux pluged in[/QUOTE]
boot with the ubuntu install cd and use the boot command ```
rescue
``` this will bring you to a terminal from there use this command
```
grub-install /dev/hda
```and reboot this should fix grub.

---

### Post by Akya on 2006-01-07
no that didnt work

---

### Post by codejunkie on 2006-01-07
do you have an ubuntu live cd handy and how are your drives setup.

---

### Post by Akya on 2006-01-07
i have linux on a 80 gig wester digitial(primary) then i installed windows on a  80 gb maxator(slave) and it messed up grub, i booed with the live cd but i cant even acces the hard drives my windows wont let me get to it and the live cd wont let me mount it

---

### Post by codejunkie on 2006-01-07
try swaping the drive order make the windows drive the master and the ubuntu drive the slave and if it still doesn't boot run grub-install /dev/hda from the install cd again.

---

