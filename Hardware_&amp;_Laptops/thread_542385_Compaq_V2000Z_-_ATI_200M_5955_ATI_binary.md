---
title: "Compaq V2000Z - ATI 200M 5955 ATI binary?"
date: 2007-09-03
forum: Hardware &amp; Laptops
---

### Post by atari05 on 2007-09-03
So I have this compaq v2000z and I have kubuntu installed and everything works fairly well. However, I'm having issues using the ATI binary to get GL running. I use adept to install the fglrx-xorg drivers, change my device section in xorg to use fglrx instead of ati, reboot and when I run fglrxinfo I get the following

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

which I know is wrong and means I'm not using he driver. So I was wondering if anyone happens to have one of these laptops and could share their experience in getting this card working with the ati driver if possible.

Once again the card is an ATI 200M 5595 and I can provide any other information that might help me getting this going!

---

### Post by nosrednaekim on 2007-09-03
you need to add the "no composite" option on the end of your Xorg.

```


Section "Extensions"
        Option      "Composite" "0"
EndSection


```

---

