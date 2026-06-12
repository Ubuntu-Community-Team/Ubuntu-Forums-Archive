---
title: "GIMP plugin help needed on Hardy 8.04"
date: 2009-02-18
forum: Installation &amp; Upgrades
---

### Post by bob12564 on 2009-02-18
I installed the Windows version of GIMP at work and found a neat plugin that I installed easily by following the Install.txt file in the ZIP download.

Now I'm home and I'm trying to install it on GIMP 2.4 on my Hardy machine.  I've never done this before and I can't figure out what to do.  

The plugin is called Wavelet and it's here:

[http://registry.gimp.org/node/4235](http://registry.gimp.org/node/4235)

I wasn't sure what to do with the wavelet-denoise-0.3.1.tar.gz file (don't even know what a .gz file is - I'm new to the Linux) but I tried downloading it and it stops at 88%.  So I went back to the Windows ZIP download and opened the Install.txt file and it said the Linux installation was done by running this command with the file
wavelet-denoise.c that's contained in the ZIP file:

gimptool-2.0 --install wavelet-denoise.c

When I run it in a terminal window it tells me there is no command gimptool-2.0.  I bet that's because I'm running GIMP 2.4.

Can anyone explain what to do in simple terms?  I appreciate the help.

---

### Post by taurus on 2009-02-18
Assuming you have downloaded the wavelet-denoise-0.3.1.tar.gz to your desktop, open a terminal and run

Applications -> Accessories -> Terminal
```
cd ~/Desktop
tar xvzf wavelet-denoise-0.3.1.tar.gz
cd wavelet-denoise-0.3.1
make <-- If there is no error message, run the next command to install it on your machine.
sudo make install
```

---

### Post by bob12564 on 2009-02-19
Thanks, but that didn't work.  Here's the terminal output:

asus-p4p800@asus-p4p800-desktop:~$ cd ~/Desktop
asus-p4p800@asus-p4p800-desktop:~/Desktop$ tar xvzf wavelet-denoise-0.3.1.tar.gz
wavelet-denoise-0.3.1/
wavelet-denoise-0.3.1/COPYING
wavelet-denoise-0.3.1/INSTALL
wavelet-denoise-0.3.1/README
wavelet-denoise-0.3.1/Makefile
wavelet-denoise-0.3.1/ChangeLog
wavelet-denoise-0.3.1/THANKS
wavelet-denoise-0.3.1/AUTHORS
wavelet-denoise-0.3.1/src/
wavelet-denoise-0.3.1/src/Makefile
wavelet-denoise-0.3.1/src/wavelet.c
wavelet-denoise-0.3.1/src/plugin.c
wavelet-denoise-0.3.1/src/denoise.c
wavelet-denoise-0.3.1/src/interface.c
wavelet-denoise-0.3.1/src/events.c
wavelet-denoise-0.3.1/src/plugin.h
wavelet-denoise-0.3.1/src/colorspace.c
wavelet-denoise-0.3.1/src/interface.h
wavelet-denoise-0.3.1/src/messages.h
wavelet-denoise-0.3.1/po/
wavelet-denoise-0.3.1/po/it.po
wavelet-denoise-0.3.1/po/Makefile
wavelet-denoise-0.3.1/po/ru.po
wavelet-denoise-0.3.1/po/et.po
wavelet-denoise-0.3.1/po/de.po
wavelet-denoise-0.3.1/po/pl.po
wavelet-denoise-0.3.1/TRANSLATIONS
asus-p4p800@asus-p4p800-desktop:~/Desktop$ cd wavelet-denoise-0.3.1
asus-p4p800@asus-p4p800-desktop:~/Desktop/wavelet-denoise-0.3.1$ 
asus-p4p800@asus-p4p800-desktop:~/Desktop/wavelet-denoise-0.3.1$ make
make -C po
make[1]: Entering directory `/home/asus-p4p800/Desktop/wavelet-denoise-0.3.1/po'
msgfmt -c -v -o de.mo de.po
make[1]: msgfmt: Command not found
make[1]: *** [de] Error 127
make[1]: Leaving directory `/home/asus-p4p800/Desktop/wavelet-denoise-0.3.1/po'
make: *** [po] Error 2
asus-p4p800@asus-p4p800-desktop:~/Desktop/wavelet-denoise-0.3.1$ 


I found this in the FAQ on the GIMP website:
-----------
How do I add new plug-ins?

First, copy the plug-in[s] to your plug-in directory (typically /usr/local/lib/gimp/$VERSION/plug-ins/).

After copying the plug-in to its proper directory, just run GIMP. It should automatically find new plug-ins.
-----------

I can see that it's not that easy!

---

