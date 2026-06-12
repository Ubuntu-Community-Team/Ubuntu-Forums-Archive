---
title: "installing graphic card driver"
date: 2013-04-05
forum: Hardware
---

### Post by archial on 2013-04-05
How to install the graphic card driver (and any other drivers), the system doesn't recognize the graphic card in the computer, what would I do to fix this ?? Thank you.[ATTACH=CONFIG]240985[/ATTACH]

---

### Post by oldos2er on 2013-04-05
What graphics card does the system have?

---

### Post by d0006 on 2013-04-06
```
sudo lspci
```
will give you a list of devices connected to a PCI bus, including your video card.
```
sudo lspci -v
```
will give you a long list.
```
sudo lspci -vv
```
will give you a really long list.

---

### Post by linrunner on 2013-04-06
Hi,

"Graphics: Unknown" is a false report and a [known bug]("https://bugs.launchpad.net/ubuntu/+source/mesa-demos/+bug/914631"). Install the package **mesa-utils** and the graphics card/driver will be shown.

---

### Post by grahammechanical on 2013-04-06
I am running 13.04 and my Details page says Graphic Unknown. And yet just a few days ago there was accurate information there about my Graphic adapter. This mis-information bug has come and gone over the last year on 12.04, 12.10. I thought it was fixed on 13.04 but it has now come back. Such is life. It is not a problem. 

The video adapter is recognised. The driver may be the Nouveau open source driver. I have found that to be acceptable but if you want a proprietary video driver or want to check what video driver is activated then in 12.10 we go to System Settings>Software Sources (called Software & Updates in 13.04) and open the Additional Drivers tab. If we have a proprietary driver installed then we get a Settings Manager for that driver in the Dash.

Regards.

---

### Post by archial on 2013-04-06
Thank you, I installed the package and the problem is solved.

---

