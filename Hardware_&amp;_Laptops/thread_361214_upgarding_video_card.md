---
title: "upgarding video card?"
date: 2007-02-14
forum: Hardware &amp; Laptops
---

### Post by icecube76 on 2007-02-14
i would like to upgrade my vga card , at the moment im using the onboard vga,,wich is not working with beryl  
yesterday i biught a nvidia card , and i got xserver error .
what should i do .
im using 6.10

regards

---

### Post by renzokuken on 2007-02-14
firstly, did you change the bios settings to use your new card?

secondly, look into installing the nvidia driver. Envy is a good way to do it [www.albertomilone.com](www.albertomilone.com) and look in the projects and guides page.

---

### Post by icecube76 on 2007-02-14
thank you renzokuken
 yes i did change the bios and i cheacked that the new card is working on livecd

---

### Post by renzokuken on 2007-02-14
well in that case the chances are it is using the wrong driver..........

boot up your machine,

wait until X crashes then press Ctrl+Alt+F1 to get into a TTY terminal

type
```
sudo nano /etc/X11/xorg.conf
```

go down to the Section "Device" part and look for the "driver" line.......

change whatever is in the exclamation marks (could be ati, radeon, i810 and a host of other things) to "vesa".

the line should now look like

```
Driver    "vesa"
```

press Ctrl+X and then Y and enter (may have that in the wrong order but the options will be at the bottom) in order to save the changes.

reboot and see what happens

---

