---
title: "Kubuntu vs. GMA4500"
date: 2011-02-14
forum: Hardware
---

### Post by Lordie on 2011-02-14
I got a laptop (Asus UL-series) with Intel GMA4500MHD graphic card. I installed Kubuntu 10.10 [64bit] on it successfully, but... it runs only in shell mode, not even trying to run graphic environment at all. Does anybody know how to fix this?

---

### Post by SeijiSensei on 2011-02-14
So, you can boot into a console, but not into the graphical interface?

After you log in, try typing "startx" at the dollar-sign prompt.  Either you'll get the GUI, or you'll see some errors reported.  If they're incomprehensible, try posting them here.  We'd probably like to see the file /etc/X11/xorg.conf as well, if you have one (you may not).

What happens if you boot directly off the Kubuntu DVD?

---

### Post by Lordie on 2011-02-14
When I load Kubuntu Live (from usb, as long as my laptop does not have cd-drive) everything works perfectly. When I type 'startx' in shell it just gives me a black screen, with no errors printed out. Another interesting point is that when I continue to work in shell - it lasts for ~5min and... gives me the same *graphical* black screen - after that only "Power" button helps. Nothing like that happens in Win7 which is also installed on the same laptop.

---

