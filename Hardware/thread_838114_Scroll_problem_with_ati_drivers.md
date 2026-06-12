---
title: "Scroll problem with ati drivers"
date: 2008-06-23
forum: Hardware
---

### Post by kozmix on 2008-06-23
Hi all, i've a new laptop with an ati hd3650 and i've installed the latest ubuntu yesterday. 

I guess it didn't detected my graphic, the resolution was awful, so i went to ati's website and downloaded the linux drivers. Installed everything according to the instructions and the resolution was awsome. Problem is, when scrolling in firefox, resizing, etc it's extremely slow. 

I've been searching the web, changed drivers, uninstall compiz, which by the way never worked, always white screen, and it's still ultra slow.

I was thinking of installed another distro, but after some search i guess it's a general problem. 

Please, could someone help? 

Thx in advance!

---

### Post by matt.taylor on 2008-06-23
I would stay away form the ATI website, use the ones you can download in Ubuntu. 

```
sudo apt-get install xorg-driver-fglrx
```

---

### Post by chalewa on 2008-06-23
does the scrolling problem happen only in firefox?

what driver did you install from the ati website?

---

### Post by matt.taylor on 2008-06-23
I couldnt remeber the URL but i have found it now, its the best for sorting out ati driver issues,

[Clicky Here]("http://wiki.cchtml.com/index.php/Ubuntu")


I have had problems with Hardy and ATI too, but nothing major:)

---

### Post by ukripper on 2008-06-23
use envy to install drivers i had this issue but was fixed using envy and then doing follwoing in terminal:
```
sudo apt-get install xorg-driver-fglrx-envy
```

restricted drivers were blurry and had glitches like that and used my procesor alot. Ati drivers worked perfectly and so much smoother with envy.

---

