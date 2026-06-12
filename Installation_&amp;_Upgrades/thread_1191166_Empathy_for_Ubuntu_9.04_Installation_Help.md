---
title: "Empathy for Ubuntu 9.04 Installation Help"
date: 2009-06-18
forum: Installation &amp; Upgrades
---

### Post by BushikuPegasus on 2009-06-18
I am a n00b when it comes to Ubuntu and so far, I've changed the theme of Ubuntu to replicate that of MAC OS X [original. i know]. 

If anyone could give me the right paths and whatnot to install it.
Thank you in advance.

---

### Post by raymondh on 2009-06-18
> **BushikuPegasus said:**
> I am a n00b when it comes to Ubuntu and so far, I've changed the theme of Ubuntu to replicate that of MAC OS X [original. i know]. 

If anyone could give me the right paths and whatnot to install it.
Thank you in advance.

You can also try mac fonts.    

For the macfonts ... in terminal (copy/paste/enter one command at a time)

```
wget http://ubuntu-debs.googlecode.com/files/macfonts.tar.gz
tar zxvf macfonts.tar.gz
sudo mv macfonts /usr/share/fonts/
sudo fc-cache -f -v
```

Then go to fonts tab (system > preferences > appearance) and change the fonts to:

Application > lucida grande
Document > lucida grande
Desktop > macGrande
window title > lucida macbold
fixed width > lucida console

Choose size to your preference.  On my system, I also changed (in DETAILS) smoothing to subpixel and hinting to none.

This was my reference for the macfonts

[http://www.ubuntu-unleashed.com/2008/05/howto-install-mac-fonts-on-ubuntu.html](http://www.ubuntu-unleashed.com/2008/05/howto-install-mac-fonts-on-ubuntu.html)


Have fun and happy ubuntu-ing

---

