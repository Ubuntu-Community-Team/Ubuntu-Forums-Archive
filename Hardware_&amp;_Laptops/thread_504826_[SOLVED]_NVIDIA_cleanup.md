---
title: "[SOLVED] NVIDIA cleanup"
date: 2007-07-19
forum: Hardware &amp; Laptops
---

### Post by univremonster on 2007-07-19
When I bought the components for my computer, I forgot about a graphics card, so as a result I was using a friend's NVIDIA card for a few weeks.  When my new card came ( FREETECH PX6200TD-128M GeForce 6200 128MB DDR PCI Express x16 Video Card), as this was my first time building a computer, I just stuck it right in the slot and it seemed to work well enough.  Since then I have had problems rendering 3D images and according to my Hardware Information page I am still using an NV43.  Unfortunately I don't have the CD that came with it or anything (though I don't think it would have been helpful since as I recall it was Windows or Mac only), is there any way to clear out all the drivers for the previous card and set this one up right?

---

### Post by jimbob on 2007-07-19
I would make sure I had installed nvidia-glx and the linux restricted modules, then save your current copy of /etc/X11/xorg.conf and use CTRL-ALT-F1 to enter single user mode as root and regenerate your xorg file ( dpkg-reconfigure -phigh xserver-xorg ) and reboot.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by univremonster on 2007-07-20
Thanks for the help:  between that and the fact that my new drivers were restricted it's working like a charm now.

---

