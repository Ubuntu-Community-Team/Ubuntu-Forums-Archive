---
title: "ATI 200M - Am I doomed to not much?"
date: 2007-05-08
forum: Hardware &amp; Laptops
---

### Post by misfitpierce on 2007-05-08
Hello. I have been using linux for awhile now... took a break from ubuntu to try Mandriva but missed ubuntu so im back. Thing is ive noticed that there is really bad ATI support for every linux distro ive tried. I have a Xpress 200m and everytime I load something even a game made for linux like X-Moto it lags so horribly bad. I can't understand why my friend has the game on his mac with intel integrated and it runs better. Is there any way to get the card going better and if so please walk me through it. I've installed latest drivers from what I know went through.

But fglrx info shows this

fghax@hax-laptop:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

Im not sure what XFree86-DRI is but I believe it may be the prob to my slow video response. Please help...

---

### Post by misfitpierce on 2007-05-08
bump... help with XFree86-DRI error and make card run better???

---

### Post by RavanH on 2007-05-11
Hi,

I've got the same issue and found that this tutorial got me on the right track: [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

At least the glxgears test (run that command from a terminal screen) before and after you get the proper drivers running, might show you improvement. Don't know about any 3D game performance though...

I'd suggest you go for the **first methode** described there, because when I tried the second - (after the first; not being satisfied with desktop-effects not working - performance dropped a bit again! And desktop-effects still do not work :(

It seems all because ATI/AMD is slow on building support for AIGLX in their driver... If you could please sign the online petition on [http://www.petitiononline.com/x200MLin/petition.html](http://www.petitiononline.com/x200MLin/petition.html) , it just might help!

Allard

---

