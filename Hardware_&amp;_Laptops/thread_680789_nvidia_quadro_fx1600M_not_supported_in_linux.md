---
title: "nvidia quadro fx1600M not supported in linux"
date: 2008-01-28
forum: Hardware &amp; Laptops
---

### Post by tricaricog on 2008-01-28
I have a new laptop  (Hp 8710w)  eqipped  with nvidia quadro fx1600M..

I installed ubuntu server, it start in text mode and when i issue startx to start graphical mode is get 

" X: cannot stat /etc/x11/X (no such file or directory), aborting ...

I think the video card is not supported ! How can I make it work ??

best regards

  Giuseppe

---

### Post by GeneralCody on 2008-02-08
Try editing your xorg.conf to use the framebuffer driver, then install the "real" nvidia driver from the restricted source.

---

### Post by CrypticDweller on 2008-02-08
With Ubuntu Server it does not install an environment other than command line. You'll need to install (if you have not already) one manually. You can use either Gnome, KDE, or xfce

gnome
```
sudo apt-get install ubuntu-desktop
```
or kde
```
sudo apt-get install kubuntu-desktop
```
or xfce
```
sudo apt-get install xubuntu-desktop
```

---

### Post by roelpeeters on 2008-02-22
Hi!

I am not sure if you already solved your problem. However it seems from other sources on the net that your problem is due to the NVIDIA drivers (or lack thereof). You could try the following link, to install the latest drivers from the NVIDIA website.

[http://littlergirl.googlepages.com/NvidiaDriverHowTo.html#toc13](http://littlergirl.googlepages.com/NvidiaDriverHowTo.html#toc13)

HTH,

Roel

---

