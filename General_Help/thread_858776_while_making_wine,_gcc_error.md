---
title: "while making wine, gcc error?"
date: 2008-07-13
forum: General Help
---

### Post by halfmike on 2008-07-13
so i'm trying to comple wine from source to fix a problem i am having in imageready and i am getting a gcc problem. can someone please help me decipher this? I did apply a patch, but i dont see wine worth using without the patch... err I dont want to give up on this and just install it from the repo. I need my imageready, lol.
```
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/halfmike/wine-1.0.0/wine-1.0.0/dlls/wtsapi32'
make[2]: Entering directory `/home/halfmike/wine-1.0.0/wine-1.0.0/dlls/winex11.drv'
../../tools/winegcc/winegcc -B../../tools/winebuild -shared ./winex11.drv.spec    bitblt.o bitmap.o brush.o clipboard.o codepage.o desktop.o dib.o dib_convert.o dib_dst_swap.o dib_src_swap.o event.o graphics.o ime.o init.o keyboard.o mouse.o opengl.o palette.o pen.o scroll.o settings.o systray.o text.o window.o wintab.o x11ddraw.o x11drv_main.o xdnd.o xfont.o xim.o xinerama.o xrandr.o xrender.o xvidmode.o     version.res  -o winex11.drv.so -lcomctl32 -luser32 -lgdi32 -ladvapi32 -limm32 -lkernel32 -lntdll -Wb,-dcomctl32 -L/usr/lib  -lXext -lX11  ../../libs/port/libwine_port.a  
/usr/bin/ld: skipping incompatible /usr/lib/libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/libXext.a when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.2.3/../../../libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.2.3/../../../libXext.a when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libXext.a when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/libXext.a when searching for -lXext
/usr/bin/ld: cannot find -lXext
collect2: ld returned 1 exit status
winegcc: gcc failed
make[2]: *** [winex11.drv.so] Error 2
make[2]: Leaving directory `/home/halfmike/wine-1.0.0/wine-1.0.0/dlls/winex11.drv'
make[1]: *** [winex11.drv] Error 2
make[1]: Leaving directory `/home/halfmike/wine-1.0.0/wine-1.0.0/dlls'
make: *** [dlls] Error 2

```

---

### Post by ramjet_1953 on 2008-07-13
Have you installed the [COLOR="Blue"]build-essential[/COLOR] package?

[COLOR="Red"]sudo apt-get install build-essential[/COLOR]

Without this meta package, you do not have the tools needed to compile.

Regards,
Roger :cool:

---

### Post by halfmike on 2008-07-13
yeah, i also have the most up-to-date gcc and g++

---

### Post by halfmike on 2008-07-14
i'm not one to bump but i was wondering if anyone could help me with this...

---

### Post by crazyguy510 on 2008-10-06
I have the same problem got to:[http://bugs.winehq.org/show_bug.cgi?id=3228](http://bugs.winehq.org/show_bug.cgi?id=3228) and see if you can make heads or tails of it then tell me what you've got. Thanks.

---

### Post by Meow27 on 2008-10-06
```
sudo apt-get build-dep wine

```
after doing that command i didnt run into any bug with make..... never tried doing make install

---

