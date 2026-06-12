---
title: "Dell C400 display problem"
date: 2005-02-12
forum: Hardware &amp; Laptops
---

### Post by rusi_pathan on 2005-02-12
Has anyone tried ubuntu on a Dell C400 (i830 graphics chipset). For some odd reason the display I get after the boot up is messed up (some odd colors show up and nothing is readable, though a faint taskbar is visible)

I tried all the possible modes after this:

"Press <RETURN> to see video modes available, <SPACEA> to continue or wait 30 secs:"

But nothing seems to work. Could it be something to do with the i830 chipset ?

Thanks in advance.

---

### Post by alastair on 2005-02-12
What is the driver used for X? i.e. 

grep -i driver /etc/X11/xorg.conf

You could try setting the driver to "vesa" in the xorg.conf file and restart X (CTRL-ALT-BACKSPACE).

---

### Post by jonhaug on 2005-06-13
During install, you can try 'linux vga=771'.  It did the trick with my C400 laptop.

---

### Post by SwinginStan on 2005-10-13
it worked out of hte box for me!

---

