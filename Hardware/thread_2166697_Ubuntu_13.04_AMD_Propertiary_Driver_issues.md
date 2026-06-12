---
title: "Ubuntu 13.04 AMD Propertiary Driver issues"
date: 2013-08-10
forum: Hardware
---

### Post by jca2323 on 2013-08-10
Hi, 

I recently built a computer and installed ubuntu onto it. Ever since I install the AMD drivers for my graphics I have been spammed with Ubuntu 13.04 encountered an internal error and the crashed program is Xorg. Any help would be greatly apperciated.

---

### Post by Ranko Kohime on 2013-08-10
Well, if Xorg actually did crash, you shouldn't be seeing a dialog box, you should be seeing a text prompt.  That being said, I experienced similar spamming regarding a variety of processes in vanilla Ubuntu, without AMD hardware (Intel laptop with integrated graphics), and this led me to ditch it in favor of my own, rather esoteric setup.

Try uninstalling the AMD drivers and see if the error occurs without.  The following commands should restore the open-source "radeon" driver:

```
sudo sh /usr/share/ati/fglrx-uninstall.sh
sudo apt-get purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev*
sudo rm /etc/X11/xorg.conf
```

Also, which version of the Catalyst Control Center did you install?

---

### Post by Mark Phelps on 2013-08-11
We need to know the make and model video chipset on your PC.  IF you don't know that info, open a terminal, enter "lspci" and look for the line containing "VGA".  Post that information back here.

Also, would be good to know the version of Ubuntu you installed.

---

### Post by jca2323 on 2013-08-11
00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Trinity [Radeon HD 7560D]
Ubuntu 13.04

Ranko,

This problem did not occur without the fglrx driver. Catalyst Control Center version 12.9

---

### Post by SweetAurora on 2013-08-11
If nothing bad seems to happen before or after the popup (like a real crash) Then you could just disable apport as a workaround. That is Ubuntu's error report manager. Just be aware that also means any other error won't get to you, but it looks like the false graphics error is the only thing popping up.

In a terminal type:
```
sudo -i gedit /etc/default/apport
```
and simply change enabled=1 to enabled=0 and then save, exit and restart. Voila! no more error popups.

---

### Post by Mark Phelps on 2013-08-12
> **jca2323 said:**
> ... This problem did not occur without the fglrx driver. Catalyst Control Center version 12.9

Then, unless you are doing 3D accelerated graphics gaming and/or need GPU temperature control, you don't NEED the fglrx driver installed.  The latest open-source Radeon drivers work quite well.

---

### Post by jca2323 on 2013-08-12
They might have worked well but fglrx gives me better performance than the open-source, sorry.

---

