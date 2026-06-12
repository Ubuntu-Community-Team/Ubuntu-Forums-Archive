---
title: "install then dead"
date: 2008-12-06
forum: Installation &amp; Upgrades
---

### Post by alzurzin on 2008-12-06
My desktop is a P4, with 1gb ram.  Video card on motherboard.  Ethernet card. Very basic.
Downloaded Ubuntu 8, and created a CD.  Installed to a separate, physical drive; under WinXP, with dual boot option.

The instal seemed to go ok: no error messages. Dual boot is ok.  Up comes the ubuntu login screen.  After entering userid and pwrd, .... nothing.  A blank screen (black), and no response from keyboard.

can anyone help, please?

---

### Post by inobe on 2008-12-06
8.04 or 8.10 ?


give us your motherboard specs, make/ model or chipset

---

### Post by alzurzin on 2008-12-06
8.10
MB has intel chipset

---

### Post by inobe on 2008-12-06
lets give this a try, startup and choose recovery mode, then choose root shell.

now run this command after you log on

```
sudo dpkg-reconfigure xserver-xorg
```

follow the onscreen directions, this should help to at least get you to the desktop.

if it works' installing your video drivers is another story.

---

### Post by alzurzin on 2008-12-06
done.  went thru the screen to select keyboard, etc. 
the effect now is an orange screen instead of black.  I can see the mouse move across the screen.
maybe I will try 8.04 instead of 8.10

---

### Post by inobe on 2008-12-06
reboot again !

also lets stay with 8.10 for now.

we are getting close, i am assuming getting it going will be easier ..

---

### Post by alzurzin on 2008-12-06
reboot does nothing.

---

### Post by inobe on 2008-12-06
lets try to reinstall ubuntu desktop

in the same shell type

> sudo apt-get install --reinstall ubuntu-desktop

---

