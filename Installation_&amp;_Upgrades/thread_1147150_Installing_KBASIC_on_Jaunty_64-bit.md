---
title: "Installing KBASIC on Jaunty 64-bit"
date: 2009-05-03
forum: Installation &amp; Upgrades
---

### Post by mickie.kext on 2009-05-03
I downloaded KBASIC (installer_kbasic_professional_linux.bin) and i tried to instal but nothing happens. I installed all dependencies I can find. Used Krusader to make file executable. Nothing. I folowed instructions from here 
[http://ubuntuforums.org/showthread.php?t=60361&page=3](http://ubuntuforums.org/showthread.php?t=60361&page=3)

I wanted to post on that topic but is apparently locked. All topic I find is about older Ubuntu releases and i386. I use 64-bit 9.04.

When I try ```
./installer_kbasic_professional_linux.bin
``` it sez 

```
./installer_kbasic_professional_linux.bin: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory
```

I tried searching for that **libqt-mt.so.3** in Synaptic, but isn't there. 

What shoul I try? Please help :confused:

EDIT: I have Qt installed.

---

### Post by mickie.kext on 2009-05-03
Please anyone?? I need KBASIC... 

I installed kubuntu-desktop via sinaptic and tried with Konqueror... nothing. Is there anyone who use KBSIC on 64-bit Jaunty? I used KBasic on Windows, and don't  want to go back to Windowz... I want it on Ubuntu.

Is there any hope?

---

### Post by mickie.kext on 2009-05-03
Nobody? I dont know what else to try...

---

### Post by StuartN on 2009-05-03
> **mickie.kext said:**
> Nobody? I dont know what else to try...

If you have already installed libqt3-mt then it is possibly looking for an older version.

---

### Post by mickie.kext on 2009-05-03
I installed correct version. Here are the dependences
> Dependencies are (shared libraries, which you must have installed on your system):

    *
      libqt-mt.so.3 &#8658; /usr/lib/libqt-mt.so.3
    *
      libXft.so.2 &#8658; /usr/lib/libXft.so.2
    *
      libQtSql.so.4 &#8658; /usr/lib/libQtSql.so.4
    *
      libQtGui.so.4 &#8658; /usr/lib/libQtGui.so.4
    *
      libpng12.so.0 &#8658; /usr/lib/libpng12.so.0
    *
      libSM.so.6 &#8658; /usr/lib/libSM.so.6
    *
      libICE.so.6 &#8658; /usr/lib/libICE.so.6
    *
      libXi.so.6 &#8658; /usr/lib/libXi.so.6
    *
      libXrender.so.1 &#8658; /usr/lib/libXrender.so.1
    *
      libXrandr.so.2 &#8658; /usr/lib/libXrandr.so.2
    *
      libXfixes.so.3 &#8658; /usr/lib/libXfixes.so.3
    *
      libXcursor.so.1 &#8658; /usr/lib/libXcursor.so.1
    *
      libXinerama.so.1 &#8658; /usr/lib/libXinerama.so.1
    *
      libfreetype.so.6 &#8658; /usr/lib/libfreetype.so.6
    *
      libfontconfig.so.1 &#8658; /usr/lib/libfontconfig.so.1
    *
      libXext.so.6 &#8658; /usr/lib/libXext.so.6
    *
      libX11.so.6 &#8658; /usr/lib/libX11.so.6
    *
      libQtCore.so.4 &#8658; /usr/lib/libQtCore.so.4
    *
      libz.so.1 &#8658; /lib/libz.so.1
    *
      libpthread.so.0 &#8658; /lib/libpthread.so.0
    *
      libdl.so.2 &#8658; /lib/libdl.so.2
    *
      libstdc++.so.6 &#8658; /usr/lib/libstdc++.so.6
    *
      libm.so.6 &#8658; /lib/libm.so.6
    *
      libgcc_s.so.1 &#8658; /lib/libgcc_s.so.1
    *
      libc.so.6 &#8658; /lib/libc.so.6
    *
      libXdmcp.so.6 &#8658; /usr/lib/libXdmcp.so.6
    *
      libXau.so.6 &#8658; /usr/lib/libXau.so.6
    *
      libexpat.so.1 &#8658; /usr/lib/libexpat.so.1
    *
      /lib/ld-linux.so.2

But I am afraid that those dependencies are only for i386. Probably are more needed packages for 64-bit

---

### Post by mickie.kext on 2009-05-05
Today was released new KBASIC 1.89f BETA

NEW Dependencies:
>     *  linux-gate.so.1
    * libQtWebKit.so.4 => /usr/lib/libQtWebKit.so.4
    * libphonon.so.4 => /usr/lib/libphonon.so.4
    * libQtSql.so.4 => /usr/lib/libQtSql.so.4
    * libQtGui.so.4 => /usr/lib/libQtGui.so.4
    * libpng12.so.0 => /usr/lib/libpng12.so.0
    * libSM.so.6 => /usr/lib/libSM.so.6
    * libICE.so.6 => /usr/lib/libICE.so.6
    * libXi.so.6 => /usr/lib/libXi.so.6
    * libXrender.so.1 => /usr/lib/libXrender.so.1
    * libXrandr.so.2 => /usr/lib/libXrandr.so.2
    * libXfixes.so.3 => /usr/lib/libXfixes.so.3
    * libXcursor.so.1 => /usr/lib/libXcursor.so.1
    * libXinerama.so.1 => /usr/lib/libXinerama.so.1
    * libfreetype.so.6 => /usr/lib/libfreetype.so.6
    * libfontconfig.so.1 => /usr/lib/libfontconfig.so.1
    * libXext.so.6 => /usr/lib/libXext.so.6
    * libX11.so.6 => /usr/lib/libX11.so.6
    * libQtNetwork.so.4 => /usr/lib/libQtNetwork.so.4
    * libQtCore.so.4 => /usr/lib/libQtCore.so.4
    * libz.so.1 => /lib/libz.so.1
    * librt.so.1 => /lib/librt.so.1
    * libdl.so.2 => /lib/libdl.so.2
    * libpthread.so.0 => /lib/libpthread.so.0
    * libstdc++.so.6 => /usr/lib/libstdc++.so.6
    * libm.so.6 => /lib/libm.so.6
    * libgcc_s.so.1 => /lib/libgcc_s.so.1
    * libc.so.6 => /lib/libc.so.6
    * libQtDBus.so.4 => /usr/lib/libQtDBus.so.4
    * libexpat.so.1 => /lib/libexpat.so.1
    * libXau.so.6 => /usr/lib/libXau.so.6
    * libxcb-xlib.so.0 => /usr/lib/libxcb-xlib.so.0
    * libxcb.so.1 => /usr/lib/libxcb.so.1
    * /lib/ld-linux.so.2
    * libdbus-1.so.3 => /lib/libdbus-1.so.3
    * libQtXml.so.4 => /usr/lib/libQtXml.so.4

And I have them all installed on correct locations. It took me half an hour to find them all... but still I can't install KBasic. Those are definitely dependencies for i386 architecture. There must be some more for AMD64. Please someone!!

---

### Post by mickie.kext on 2009-05-09
Up

---

### Post by Yellow Pasque on 2009-05-10
I'm guessing that the program you're trying to install is a 32-bit one, which can't use the 64-bit shared libraries.

Use getlibs: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

### Post by Agg23 on 2009-05-29
Did anyone solve this?  If so, how did you do it?  I've tried several suggestions but nothing works :(

---

### Post by Yellow Pasque on 2009-05-30
Install getlibs as suggested: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)
Then:
```
sudo getlibs installer_kbasic_professional_linux.bin
```

---

### Post by Agg23 on 2009-05-30
Thank you ;)

It installed but now I can't get it to launch.  :(

---

### Post by TiddlyPom on 2009-09-30
This worked for me:

1) sudo getlibs installer_kbasic_professional_linux.bin
2) chmod a+rx installer_kbasic_professional_linux.bin
3) sudo ./installer_kbasic_professional_linux.bin (install to /opt/kbasic)
4) sudo getlibs /opt/kbasic/kbide
5) rm -f /root/Desktop/*.desktop (or remove KBasic [.desktop] files individually)
6) sudo gedit /usr/share/applications/KBasic.desktop (paste the text below in and save it)

[Desktop Entry]
Encoding=UTF-8
Version=1.0
Exec=/opt/kbasic/kbide
Icon=/opt/kbasic/ide/kbasic.png
Terminal=false
Name=KBasic
Comment=KBasic Development Environment
Type=Application
Categories=Development;
StartupNotify=true

Voila!  KBasic should have appeared in Applications/Development and should work fine :)

---

