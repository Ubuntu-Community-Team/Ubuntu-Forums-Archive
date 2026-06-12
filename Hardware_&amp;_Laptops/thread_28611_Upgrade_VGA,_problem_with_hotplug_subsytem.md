---
title: "Upgrade VGA, problem with hotplug subsytem"
date: 2005-04-20
forum: Hardware &amp; Laptops
---

### Post by pablo.aimar on 2005-04-20
I've installed Hoary (5.04) a week ago. It run smoothly.  ;-) 
Yesterday, i've upgraded VGA card from internal VGA (onboard) to GeForce MX 440 SE. Then, while ubuntu boot, it freeze when entering hotplug system.  :-x 
When i try to remove hotplug form /etc/init.d, the system could not continue boot process.

Till now, i can't get in to my ubuntu system.

Anyone can help me ?? i'm stuck  :?  ](*,)

---

### Post by diebels on 2005-04-21
You need to get hotplug back. Boot with a live cd, chroot into the ubuntu partition and reinstall hotplug. Can you press control+c to get past the hotplug freeze. Also remove quiet from the kernel command line in /boot/grub/menu.lst so you can see more messages

---

### Post by pablo.aimar on 2005-04-21
i've reinstalled the hotplug, but it still freeze when boot. i can't press ctrl+c to get past the hotplug freeze, it  just ... freeze .. hang maybe.

any idea ??

UPDATE :

I've decided to reinstall the system, and then when it comes first boot process, before configuring the packages, it freeze, just when starting hotplug subsystem.

i think it is another bugs, maybe .. or just hardware conflict between geforce 4 and intel integrated vga card (i810 chipset).

 :?

---

