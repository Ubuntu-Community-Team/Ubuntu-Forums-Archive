---
title: "Mic not working after 12.4 Compac Presario CQ50"
date: 2012-05-13
forum: Hardware
---

### Post by toogooda on 2012-05-13
Internal Mic not working on this laptop after install of 12.4, last version was 11.4.

The following is detailed information about my sound card that I got running a script.

[http://www.alsa-project.org/db/?f=46583e01530afc82ffddef6d02a60faed52dcca0](http://www.alsa-project.org/db/?f=46583e01530afc82ffddef6d02a60faed52dcca0)

Can anyone help please?

---

### Post by sirriffsalot on 2012-05-13
Bruuu bruuu brrruuhm!

Have you done the usual of checking if any installed mixers are conflicting or simply muting it? Check the gnome mixer and the alsamixer in terminal and compare notes? - Run ```
alsamixer
``` in terminal for  alsamixer

---

### Post by toogooda on 2012-05-13
Yes not muted in settings but not sure how to use alsamixer I get a screen I don't understand
The bar for "Mic Boos" is blank and has value of 0<>0.

---

### Post by toogooda on 2012-05-13
Playing around I got it to show me this for Mic

Card: HDA NVidia                                        
Chip: Nvidia MCP77/78 HDMI                   
Item: Mic Boost [dB gain: 0.00, 0.00]

---

