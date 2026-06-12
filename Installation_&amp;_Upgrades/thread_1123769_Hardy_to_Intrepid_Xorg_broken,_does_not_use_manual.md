---
title: "Hardy to Intrepid: Xorg broken, does not use manual edited xorg.conf anymore"
date: 2009-04-12
forum: Installation &amp; Upgrades
---

### Post by wolfchri on 2009-04-12
Hello there,

my mother's PC was running fine on Hardy. I made the mistake to update it to Intrepid, and now, the graphics are broken...

Hardware:
Belinea 10 30 40 CRT screen
i945 graphics in chipset
i386

Right after the update, xorg put the screen into a mode that it was not able to sync ("out of range") - very bad. With some Ctrl-Alt-Backspace magic, I got the screen back, but at 640x480/vesa.

Running displayconfig-gtk resulted in a emergency desktop message - but when I now click OK 3 times, I get the manually set up xorg.conf, with i810 driver and Belinea settings, 87 Hz. refresh rate. 

xorg error message is that screen devices is not found during initial start of xorg. The repsective section is, however existent in xorg.conf, pointing to the Belinea settings. 

So my problem is basically how can I make xorg use the manually changed /etc/xorg.conf without trying the automatic settings first, where it does not detect the screen?

---

