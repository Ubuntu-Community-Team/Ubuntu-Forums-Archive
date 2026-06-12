---
title: "No DejaVu Sans Condensed font"
date: 2008-08-15
forum: General Help
---

### Post by capo1949 on 2008-08-15
Hi
A newbie here

Using 8.04, no font as above, is there some way I can download it?

I need it to print greek characters, as any other font i have tried the spacing is no good and unreadable.

Thanks in anticipation
Graham

see for great font [http://ubuntu.wordpress.com/2007/05/21/300-easily-installed-free-fonts-for-ubuntu/](http://ubuntu.wordpress.com/2007/05/21/300-easily-installed-free-fonts-for-ubuntu/)

---

### Post by mannheim on 2008-08-15
The font should be installed in a default Ubuntu installation. It is installed as part of the package "ttf-dejavu-extra".

You can see whether the actual font file is on your system. Opena terminal and list the contents of the relevant directory with:
```

ls /usr/share/fonts/truetype/ttf-dejavu/

```
You should see the font listed there as DejaVuSansCondensed.ttf. If it isn't there, install the package "ttf-dejavu-extra" using Synaptic.

---

### Post by capo1949 on 2008-08-15
hi 
thx for you help
graham

---

