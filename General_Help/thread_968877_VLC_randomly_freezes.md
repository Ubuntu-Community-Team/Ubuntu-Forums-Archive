---
title: "VLC randomly freezes"
date: 2008-11-03
forum: General Help
---

### Post by MarshyTheKid on 2008-11-03
VLC sometimes has the image freeze on me until I hit pause and play again. It happens about every 20 or 30 seconds.
Any ideas as to why?

---

### Post by MarshyTheKid on 2008-11-05
Any help?

---

### Post by MarshyTheKid on 2008-11-05
```
VLC media player 0.9.4 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed
QPainter::begin: Paint device returned engine == 0, type: 1
[00000420] avcodec decoder error: more than 5 seconds of late video -> dropping frame (computer too slow ?)

```
Thats what I get when I run it.

---

### Post by scouser73 on 2008-11-05
I've no ideas as to why it is happening to but you're not the only one, I have 9.4 too and it's really annoying.

---

### Post by Meow27 on 2008-11-05
you might want to try the new version.

try this:

download the source code of VLC from the VLC site

extract the vlc folder into your home folder...

run this in the terminal
```
sudo apt-get build-dep vlc
```
these are the dependencies needed to compile as well as to run vlc

in the termial
```
cd vlc-0.9.5
```(or whatever the folder is)
once the terminal shows that you are on that folder, type ```
./configure
``` this should work for intrepid but for hardy you might need to do this
```
./configure --disable live555
``` (you might need a dash in between disable and live555... i dont remember... the configure script tells you if you need to do so)
if the configure script succeeds. then in the terminal, type
```
make
```

this will take a while, and once you are done you go into the vlc folder and double click vlc and you should be able to run the new version 


i dont want to make this more complicated but if this works for you i can tell you how to have it installed.


***Disclaimer: i cant be held responsible for any damage that can happen through this guide***

hope this helps

(as a side note i think that the new one looks like BSplayer)

---

### Post by Shagg on 2008-11-10
Thanks, Meow27!

I had the same issue, today I tried what you said (using vlc 0.9.6 instead of 0.9.5) and, until now, it seems to have solved the problem. 

BTW, there's a typo, where it says 

```
/.configure
```

it should say 

```
./configure
```

Hope this helps, and thanks again.

---

### Post by Meow27 on 2008-11-10
lol sry about that... ill fix it :P

---

### Post by maximalistic on 2008-11-16
hi i have the same freeze problem and wanted to try vlc 0.9.6 to see if that helped but when i do :
sudo apt-get build-dep vlc
i get :
E: Unable to find a source package for vlc

and i guess thats why it doesnt work to configure because i get this:
configure: error: Could not find libmad on your system

---

### Post by Meow27 on 2008-11-20
start up synaptic package manager

search libmad

click on libmad 
and 
libmad-dev

you might have to repeat similar instructions through configure to get it all set up

---

