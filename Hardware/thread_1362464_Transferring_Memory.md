---
title: "Transferring Memory"
date: 2009-12-23
forum: Hardware
---

### Post by HarrisonVR on 2009-12-23
[FONT="Verdana"]Hey,

I used Wubi to install Ubuntu, so I still have Vista installed on my PC. I want to transfer some of the files, or the free space that Vista is using currently, over to my Ubuntu so I can install more programs and games etc.

Is there anyway to transfer say, 5000kb over to Ubuntu so I install a game on Steam in Ubuntu?

All help appreciated, thanks a lot
Harrison[/FONT]

---

### Post by IcarusR on 2009-12-23
I assume you mean resize the partitions.

You can boot from 'live CD' & use Gparted to resize partitions.

Aplicatios > Accessories > Terminal & type

```
sudo gparted
``` 

Instructions resizing partitions from gparted web site

[http://gparted.sourceforge.net/larry/resize/resizing.htm]("http://gparted.sourceforge.net/larry/resize/resizing.htm")

---

