---
title: "Ubuntu wont start"
date: 2007-10-23
forum: Hardware &amp; Laptops
---

### Post by Bishop Hill on 2007-10-23
Ive got a huge problem. A couple of hours ago I tried to install curves for AWN, and ended up rebooting my computer in the progress. But suddenly, nothing happends. 

The system gives me the HP bootscreen, GRUB and it even says that the kernel is alive, but the screen goes black (which is usually does on startup, but after a minute or two the login screen appears), and it stays that way, without any loginscreen. I think that the graphical interface (I think its called xserver) has been configured in some way. 

I can start in recovery mode and with a live cd, so if anyone knows how to fix this I would be endlessly grateful.

edit I have gutsy gibbon on a HP laptop with a ATI MOBILITY RADEON Xpress 200 Series graphics card)

---

### Post by be4truth on 2007-10-23
Boot into recovery mode:

```
dpkg-reconfigure xserver-xorg
```

Follow the wizard to configure your graphic settings.

---

### Post by Bishop Hill on 2007-10-23
> **be4truth said:**
> Boot into recovery mode:

```
dpkg-reconfigure xserver-xorg
```file:///usr/share/ubuntu-artwork/home/index.html

Follow the wizard to configure your graphic settings.


When the guide comes to the selection of bits, and I press enter, and the recoverymode terminal reappears. I tried to reboot, but nothing changed. What did I do wrong?

---

### Post by be4truth on 2007-10-23
You can go with the suggested solutions from the wizard expect you now better. Try to run the wizard again and follow the defaults. It isn't sure that will fix your problem but xserver problem can be solved that way. 
Try to look in the forum for GDM Gnome Desktop Manager. That can be the other problem that comes to me.

---

### Post by Bishop Hill on 2007-10-23
> **be4truth said:**
> You can go with the suggested solutions from the wizard expect you now better. Try to run the wizard again and follow the defaults. It isn't sure that will fix your problem but xserver problem can be solved that way. 
Try to look in the forum for GDM Gnome Desktop Manager. That can be the other problem that comes to me.

Will try that. Thank you for your help=)

---

### Post by Bishop Hill on 2007-10-23
I figured out what the problem is, I think. The bit-part is the last step, and I think ubuntu wants me to backup xorg.conf. How do I do that?

---

### Post by be4truth on 2007-10-23
Everytime you use the wizard it backups the file automatically.

---

