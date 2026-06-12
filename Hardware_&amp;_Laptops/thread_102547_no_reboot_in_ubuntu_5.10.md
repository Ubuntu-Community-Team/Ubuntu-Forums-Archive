---
title: "no reboot in ubuntu 5.10?"
date: 2005-12-12
forum: Hardware &amp; Laptops
---

### Post by Ana Carolina on 2005-12-12
Hi.
I have a toshiba satellite A45 series and I tried to install ubuntu 5.10 but it doesn't reboot!
In all aptempts to restart the computer from ubuntu, the computer freezes with a black screen.
The grub function works well when I reboot from windows.

Can someone help me?

Thanks,
Ana

---

### Post by earobinson on 2005-12-12
try sudo shutdown -r 0 (I hope that is the syntax windows :() see if that works

---

### Post by Ana Carolina on 2005-12-12
Hi...
Thanks but this also doesn't work...
Still freezes with a black window :(

---

### Post by earobinson on 2005-12-12
I have seen another thread refering to this as a bug, I am unable to find that thread right now, Have u updated recently. ps, holding your power button down for 5ish seconds should power down your computer instead of unpluging it.

---

### Post by Gray. on 2005-12-12
how about ```
sudo init 6
```

---

### Post by bonsiware on 2005-12-13
Try to add 'nolapic' parameter in /boot/grub/menu.lst at the end of your kernel line...

---

### Post by kairu0 on 2005-12-13
I had exactly the same symptoms on my Sony Vaio until I added "reboot=h" to the options line in Grub.

---

### Post by Ana Carolina on 2005-12-13
[QUOTE=kairu0]I had exactly the same symptoms on my Sony Vaio until I added "reboot=h" to the options line in Grub.[/QUOTE]

Hey...
Thanks, this worked just fine :D

---

