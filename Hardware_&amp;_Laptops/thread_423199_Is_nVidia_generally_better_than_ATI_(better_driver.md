---
title: "Is nVidia generally better than ATI (better drivers)?"
date: 2007-04-25
forum: Hardware &amp; Laptops
---

### Post by jespdj on 2007-04-25
Hello,

I currently have an ATI X1600 video card in my computer. Everything works, I am using the fglrx driver, Xgl and Compiz - it all works without problems. I have one minor thing and that is that I can't run fgl_glxgears normally; if I try I get:

Using GLX_SGIX_pbuffer
Xlib:  extension "XFree86-DRI" missing on display "localhost:1.0".
Error: couldn't get fbconfig

This is because Xgl is running on display 1 and not on display 0, which is what fglrx is using (?). I am running Xgl on display 1 because that is what [this wiki page about Xgl](https://wiki.ubuntu.com/CompositeManager/Xgl) told me to do, and indeed if I run it on display 0 then it will not start. I can run fgl_glxgears when I tell it to use display 0: "fgl_glxgears -display 0:0" - But then the window with the rotating cube doesn't have any border or title bar.

So far I have the impression that ATI's drivers for Linux are not great and that they are especially lacking some OpenGL features. Is that indeed the case?

I am contemplating getting a different video card, an nVidia 8600GTS. Are nVidia's Linux drivers better, especially with regard to 3D graphics / OpenGL? Or can I expect lots of limitations that need workarounds just like with ATI's driver?

(I'm using Feisty Fawn 64-bit).

---

### Post by mrpaco on 2007-04-26
In my experience, nVidia is a lot better under Linux than ATI is.  However, an 8600GTS is more than likely too new of a card to have driver support under Linux (especially under 64-bit; I could be wrong though).  Perhaps go with a similarly priced 7900 part, unless DX10 is a concern.

---

### Post by Concrete on 2007-04-26
Like a @mrpaco say nVidia is a lot better under Linux (and M$) than stupid ATi.

I have GeForce 8800GTS (320mb) and i must spend day and night to find, compile, setting and make that my card works just fine, but im succeed and this all on 6.10 whitout any generic driver i work on terminal only, but this new version 7.04 have generic driver for 8800 than u can easily download and install driver :)

And my recommendation to you @jespdj is NVIDIA NVIDIA and only NVIDIA!

---

### Post by swp6499 on 2007-05-01
maybe late but i have an msi nvidia 8600gts using the new beta driver and havent had any problems with it at all in ubuntu running feisty and beryl all the time.......hope this helps

---

### Post by enzobelmont on 2007-05-02
my two cents:

ati radeon xpress 200m= i spent two days in my life installing drivers. All went OK.


nvidia geforce fx5200= my little sister help me in setup process, estimated time: 4 minutes. All went OK.

ati propietary drivers performance= simply SUCKS

nvidia propietary drivers performance= same as windows (maybe slightly faster).


if you use linux stay AWAY from ati.

sorry my english... :)

---

### Post by davin on 2007-05-02
hey i used ati x1300 it detected but when i used 6800gt but it not detected.

---

### Post by enzobelmont on 2007-05-02
hey are you from this planet???

are you using ATI's own drivers or generic ones?

---

### Post by EXCiD3 on 2007-05-03
My friend and i have been experimenting with Linux alot lately and we have had much better luck with NVIDIA over ATI. I love the NVIDIA driver that Automatix2 installed as it is nearly the same as my Windows driver.

---

