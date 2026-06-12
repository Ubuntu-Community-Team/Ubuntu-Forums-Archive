---
title: "Error when Installing Creative Sound Blaster X-Fi Linux driver in xubuntu 11.04"
date: 2011-10-01
forum: Hardware
---

### Post by josephts7@hotmail.com on 2011-10-01
[SIZE=3]I get a Error when Installing Creative Sound Blaster X-Fi Linux driver.
What drivers xfi [/SIZE]ALSA?
[SIZE=3] How get this ( XFiDrv_Linux_Public_US_1.00.tar.gz )  driver installed in Xubuntu 11.04 without errors?[/SIZE]  

**[SIZE=4]Terminal:[/SIZE]**
                       #toc, .toc, .mw-warning { border: 1px solid  rgb(170, 170, 170); background-color: rgb(249, 249, 249); padding: 5px;  font-size: 95%; }#toc h2, .toc h2 { display: inline; border: medium  none; padding: 0pt; font-size: 100%; font-weight: bold; }#toc #toctitle,  .toc #toctitle, #toc .toctitle, .toc .toctitle { text-align: center;  }#toc ul, .toc ul { list-style-type: none; list-style-image: none;  margin-left: 0pt; padding-left: 0pt; text-align: left; }#toc ul ul, .toc  ul ul { margin: 0pt 0pt 0pt 2em; }#toc .toctoggle, .toc .toctoggle {  font-size: 94%; }body { font-family: 'Times New Roman'; color: rgb(0, 0,  0); widows: 2; font-style: normal; text-indent: 0in; font-variant:  normal; font-weight: normal; text-decoration: none; text-align: left;  font-size: 12pt; }table {  }td { border-collapse: collapse; text-align:  left; vertical-align: top; }p, h1, h2, h3, li { color: rgb(0, 0, 0);  font-family: 'Times New Roman'; font-size: 12pt; text-align: left; }      
[LEFT]**[COLOR=Red]exdesktop@ubuntu:~/XFiDrv_Linux_Public_US_1.00$ make[/COLOR]**[/LEFT]
    [LEFT]**[COLOR=Red]make -C /lib/modules/2.6.38-11-generic/build M=/home/exdesktop/XFiDrv_Linux_Public_US_1.00[/COLOR]**[/LEFT]
    [LEFT][COLOR=Red]m[/COLOR]**[COLOR=Red]ake[1]: Entering directory `/usr/src/linux-headers-2.6.38-11-generic'[/COLOR]**[/LEFT]
    [LEFT]**[COLOR=Red]  LD      /home/exdesktop/XFiDrv_Linux_Public_US_1.00/built-in.o[/COLOR]**[/LEFT]
    [LEFT]**[COLOR=Red]  CC [M]  /home/exdesktop/XFiDrv_Linux_Public_US_1.00/xfi.o[/COLOR]**[/LEFT]
    [LEFT]**[COLOR=Red]/home/exdesktop/XFiDrv_Linux_Public_US_1.00/xfi.c:14:26:_[COLOR=Magenta] fatal error: [/COLOR]_sound/driver.h: No such file or directory[/COLOR]**[/LEFT]
    [LEFT]**[COLOR=Red]compilation terminated.[/COLOR]**[/LEFT]
    [LEFT]**[COLOR=Red]make[2]: *** [/home/exdesktop/XFiDrv_Linux_Public_US_1.00/xfi.o] Error 1[/COLOR]**[/LEFT]
    [LEFT]**[COLOR=Red]make[1]: *** [_module_/home/exdesktop/XFiDrv_Linux_Public_US_1.00] Error 2[/COLOR]**[/LEFT]
    [LEFT]**[COLOR=Red]make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-11-generic'[/COLOR]**[/LEFT]
    [LEFT]_[COLOR=Magenta]**make: *** [all] Error 2**[/COLOR]_[/LEFT]
    [LEFT]**[COLOR=Red]exdesktop@ubuntu:~/XFiDrv_Linux_Public_US_1.00$ sudo make install[/COLOR]**[/LEFT]
    [LEFT]**[COLOR=Red]Copy module files...[/COLOR]**[/LEFT]
    [LEFT]**[COLOR=Red]cp: cannot stat `ctxfi.ko': No such file or directory[/COLOR]**[/LEFT]
    [LEFT]**[COLOR=Red]make: *** [COLOR=Magenta]_[install] Error 1_[/COLOR][/COLOR]**[/LEFT]
    [LEFT]**[COLOR=Red]exdesktop@ubuntu:~/XFiDrv_Linux_Public_US_1.00$ [/COLOR]**[/LEFT]

---

### Post by Toz on 2011-10-07
Have a look at this link: [http://ubuntuforums.org/showthread.php?t=1817930]("http://ubuntuforums.org/showthread.php?t=1817930"). There may be no need to compile.

What does:
```
lspci -k | grep -A 3 Audio
```return?

---

