---
title: "[SOLVED] weak graphic performance..."
date: 2008-08-07
forum: Hardware
---

### Post by fedra88 on 2008-08-07
i've just installed xubuntu on an old pc... everything is ok, but the maximum screen resolution is 800x600. i don't know which graphic card i'm using (it's an old pci, ATI)...
can xubuntu detect and identify that card? how can i change these settings? 
xubuntu seems to have less tools/settings than ubuntu, i can't really find anything helpful...

---

### Post by overdrank on 2008-08-07
> **fedra88 said:**
> i've just installed xubuntu on an old pc... everything is ok, but the maximum screen resolution is 800x600. i don't know which graphic card i'm using (it's an old pci, ATI)...
can xubuntu detect and identify that card? how can i change these settings? 
xubuntu seems to have less tools/settings than ubuntu, i can't really find anything helpful...

Use the command in the terminal ```
lspci
``` to identify the graphics. Have you tried the display setting under applications?

---

### Post by fedra88 on 2008-08-08
the grafic card is an ATI 3D Rage Pro 215GP.

800x600@56 Hz is the maximum resolution allowed by screen preferences.
should i download any drivers, or manually edit any files...?

---

### Post by overdrank on 2008-08-08
> **fedra88 said:**
> the grafic card is an ATI 3D Rage Pro 215GP.

800x600@56 Hz is the maximum resolution allowed by screen preferences.
should i download any drivers, or manually edit any files...?

You can try and use the alt, F2 keys and enter this command ```
gksu displayconfig-gtk
``` and adjust the resolution there. The ati card and is rather outdated and the drivers should be included with the install.

---

### Post by fedra88 on 2008-08-08
the whole pc is outdated ;)

anyway,

```
(gksu:5219): Gtk-WARNING **: cannot open display: 
```

---

### Post by overdrank on 2008-08-08
> **fedra88 said:**
> the whole pc is outdated ;)

anyway,

```
(gksu:5219): Gtk-WARNING **: cannot open display: 
```

My apologies, My xubuntu is install on a Ubuntu system. You can use synaptic manger search and install
displayconfig-gtk
This may help with the resolution.

---

### Post by fedra88 on 2008-08-09
don't worry... it's xubuntu fault :D

now i'm learning to use synaptic without an internet connection... i'll let you know as soon as possible!
thank you for your support!

---

### Post by fedra88 on 2008-08-10
done :)
everything is ok now!

thanks

---

