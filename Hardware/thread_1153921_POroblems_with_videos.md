---
title: "POroblems with videos"
date: 2009-05-09
forum: Hardware
---

### Post by W0T4N on 2009-05-09
Please I need help. I am noob in ubuntu and I have this kind of problem:
I just bought a extrenal monitor LG Flatron W 1934S set the resolution everything is fine, but when i start the viedo it just flush and close when i type in  console this is result : 

laufem@laufem-laptop:~$ vlc '/home/laufem/Pracovná plocha/X-Men.Origins.Wolverine.2009.WORKPRINT.XviD-NoGRP.avi' 
VLC media player 0.9.9a Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.9a Grishenko - (c) 1996-2009 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintainer-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=2ubuntu1' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-realrtsp' '--disable-dv' '--enable-x264' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "sk"
[00000001] main libvlc: Spustenie programu VLC s predvolený vzh&#318;adom a rozhraním. Pre spustenie bez rozhrania a vzh&#318;adu zadajte 'cvlc'
/home/laufem/.themes/Dust/gtk-2.0/gtkrc:79: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/laufem/.themes/Dust/gtk-2.0/gtkrc:80: Murrine configuration option "lightborder_ratio" will be deprecated in future releases. Please use "lightborder_shade" instead.
/home/laufem/.themes/Dust/gtk-2.0/gtkrc:95: Murrine configuration option "style" is not supported and will be ignored.
/home/laufem/.themes/Dust/gtk-2.0/gtkrc:226: Murrine configuration option "style" is not supported and will be ignored.
/home/laufem/.themes/Dust/gtk-2.0/gtkrc:336: Murrine configuration option "style" is not supported and will be ignored.
/home/laufem/.themes/Dust/gtk-2.0/gtkrc:370: Murrine configuration option "style" is not supported and will be ignored.
[????????] x11 video output error: X11 request 132.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  132 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  84
  Current serial number in output stream:  85



my lspci
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

---

### Post by whoop on 2009-05-16
Do you have an on-board video-card (ah wait you do)? How much ram do you have? Are you utilizing swap on a regular/default basis?
My point is. You might have a ram problem (to little or currupt) and you video adapter uses that ram.

---

