---
title: "Cannot get scanner to work, please help"
date: 2017-06-11
forum: Hardware
---

### Post by brucey2343 on 2017-06-11
Hi guys,

I have a Canon MG3550 scanner and printer AIO. I got the printer working (eventually, after installing so many different drivers etc.) but the scanner doesnt work.

I have installed Scangearmp for my scanner, the driver from Canon. When I try to run Skanlite, it searches, the for half a second flashes up with the scanner name, then a dialog box opens saying "Opening the selected scanner failed" then closes Skanlite.

Does anyone have any idea how I can fix this? I need my scanner as soon as possible.

Thanks guys!

---

### Post by pdc on 2017-06-11
so you must be running KDE; I googled on Skanlite and it seemed to be a KDE product; and seems based on sane; the open-source product for scanners; 

they think your 5300series device should be completely supported; [http://www.sane-project.org/sane-mfgs.html#Z-CANON](http://www.sane-project.org/sane-mfgs.html#Z-CANON) ........... what does ```
lsusb
``` give in a terminal please? It should say ```
04a9:1754
```

_____________
can I suggest you join the sane mailing list; tell them your problem; they are the experts; they can hopefully help you; [http://lists.alioth.debian.org/mailman/listinfo/sane-devel](http://lists.alioth.debian.org/mailman/listinfo/sane-devel)   ....a very helpful group; please let us know of your results

_________

ScanGearMP from Canon is a different programme; try running it with ```
scangearmp
``` in a terminal; you can set up a launcher to ... launch it if all is good

---

### Post by brucey2343 on 2017-06-11
wow, the running from console worked! Thank you so much!!!

---

### Post by pdc on 2017-06-12
thanks; glad it is going; you can keep using the terminal or create a launcher

this used to work [http://www.codemarvels.com/2012/05/create-shortcut-launcher-on-desktop-on-ubuntu-12-04/](http://www.codemarvels.com/2012/05/create-shortcut-launcher-on-desktop-on-ubuntu-12-04/)

so the commands are

 ```
sudo apt install gnome-panel
```

```
gnome-desktop-item-edit ~/Desktop/ --create-new
``` and with the box that appears, the command must be ```
scangearmp
``` but the other bits you can name them as you see fit ......

______--

the images with ScanGearMP can be large; if one imports the images into GiMP; and then uses the EXPORT function, one can select JPEG and shrink the image size a lot

---

