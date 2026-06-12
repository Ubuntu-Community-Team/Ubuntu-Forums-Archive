---
title: "Keyboard Layout"
date: 2005-06-11
forum: Hardware &amp; Laptops
---

### Post by rockett15 on 2005-06-11
Hi Folks,

I have been using a british keyboard for as long as I can remember and set-up Ubuntu with that. However, I got a new pc and moved my british keyboard over to that one. Because I can't get another british keyboard in Canada I have to use a US keyboard on my Ubuntu system now. I changed the keyboard layout in the GNOME settings and in the xorg.conf, however that is just for X. How do I change the keyboard layout in the terminal? It is still coming up with the other layout.

Thanks  :)

---

### Post by FizDev on 2005-06-12
Hello,
I believe I can help you.
Execute the command "sudo loadkeys uk", you're keyboard layout in the console should be british!  ;-) 

You can go to /usr/share/keymaps/i386/
You'll see a list of disponible keymaps, the one you want is uk.kmap.gz (I think so)

---

