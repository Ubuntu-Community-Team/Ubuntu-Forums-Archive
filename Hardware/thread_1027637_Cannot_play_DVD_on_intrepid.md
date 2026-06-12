---
title: "Cannot play DVD on intrepid"
date: 2009-01-01
forum: Hardware
---

### Post by cmSthlm on 2009-01-01
Hello!

I cannot play DVDs on my Sony Vaio VGN-TX3XP under Ubuntu 8.10. I have installed the "restricted extras" and I do have the libdvdread3 package installed. 

The DVD-disc shows up at the Desktop but Totem or VLC just closes a second after opening. 

Is there any checklist to verify all components needed to play DVDs?

Thanks
/M

---

### Post by balloooza on 2009-01-01
unless you bought it from dell, sory, out of luck, this is illegal.
You can however play dvds that you burnt (EX home movies, data dvds)

DVDs DO work, but playing encrypted dvds dosn't

[http://shop.canonical.com/product_info.php?products_id=243](http://shop.canonical.com/product_info.php?products_id=243)
this would allow you too :)

---

### Post by cmSthlm on 2009-01-01
Thank you, balloooza for your reply.

But is there really no way of circumventing this? I thought by installing the appropriate packages and codecs it would be possible. I realize that Ubuntu cannot be distributed for free with support for commercial dvds, but is every Ubuntu user playing DVDs on their laptops using PowerDVD Linux?

Thanks again
/M

---

### Post by redsoxreed on 2009-01-01
You need libdvdcss2.  It's technically illegal in the United States to decrypt DVDs, but it's not hard to find.

---

### Post by cmSthlm on 2009-01-01
I installed this with

 sudo apt-get install libdvdread3 gstreamer0.10-plugins-ugly

and then

 sudo /usr/share/doc/libdvdread3/install-css.sh


But it had no effect...

/M

---

### Post by Kevbert on 2009-01-01
It may be worth installing Quickstart which will install most of the codecs/drivers that you need. See my signature for the link.

---

### Post by redsoxreed on 2009-01-01
Add the medibunto repository to your sources list.  There's instructions on the website on how to do this.

[http://www.medibuntu.org/](http://www.medibuntu.org/)

Then, sudo apt-get install libdvdcss2

---

### Post by euchrid33 on 2009-01-11
> **redsoxreed said:**
> Add the medibunto repository to your sources list.  There's instructions on the website on how to do this.

[http://www.medibuntu.org/](http://www.medibuntu.org/)

Then, sudo apt-get install libdvdcss2

This sorted out my problem, thank you very much.

---

### Post by cmSthlm on 2009-01-17
Thank you guys for your efforts. I tried adding Medibuntu to the repositories and I tried with Quickstart, but the problem remains. 

The window opens but after a second it closes again. If a open the DVD I can see the miniature images of the video files. I can play CD-records.

So I guess there's some other problem. Does anyone have any suggestion for troubleshooting?


Best,
CM

---

### Post by redsoxreed on 2009-01-17
Launch totem or vlc (whatever you're using) from the command line.  When the window closes, post whatever it spits out into the terminal.

---

### Post by cmSthlm on 2009-01-17
Ok!

vlc gave the following

```
VLC media player 0.9.4 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "sv"
```




When I try 

```
vlc /media/cdrom0 
```

I get:

```
VLC media player 0.9.4 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "sv"
[00000001] main libvlc: Kör vlc med standardgränssnittet. Använd "cvlc" för att använda vlc utan gränssnitt.
libdvdnav: Using dvdnav version 4.1.2 from http://dvd.sf.net
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/marcus/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions: 2
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
[00000457] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:448000
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[????????] x11 video output error: X11 request 140.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  85
  Current serial number in output stream:  86
```

---

### Post by redsoxreed on 2009-01-17
It looks like vlc doesn't think it's a DVD. Vlc should be able to detect DVDs even without dvd decrypting libraries such as libdvdcss2.  Are you sure it's mounted in /media/cdrom0?  It could be under /media/"whatever the name of the DVD volume is"

---

