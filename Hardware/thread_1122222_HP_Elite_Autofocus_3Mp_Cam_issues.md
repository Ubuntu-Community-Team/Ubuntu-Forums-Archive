---
title: "HP Elite Autofocus 3Mp Cam issues"
date: 2009-04-10
forum: Hardware
---

### Post by allen.smith81 on 2009-04-10
Hi all,

Having some problems getting my new webcam working and cant find anything about it anywhere.

Its the HP Elite Autofocus 3MP webcam.

any help would be appreciated.

lsusb shows

```
Bus 001 Device 004: ID 0ac8:c315 Z-Star Microelectronics Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 046d:c219 Logitech, Inc. Cordless RumblePad 2
Bus 002 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

the cam seems to be the Z Star Microelectronics Corp

this is the message from dmesg

```
[   13.645409] uvcvideo: Found UVC 1.00 device HP 3-MegaPixel Webcam GX607AA (0ac8:c315)
[   13.649389] input: HP 3-MegaPixel Webcam GX607AA as /devices/pci0000:00/0000:00:02.1/usb1/1-4/1-4:1.0/input/input6

```

which seems like its not mapping it to /dev/video0

cat /dev/video0 produces a message saying no such device.

any help would be appreciated.

---

### Post by allen.smith81 on 2009-04-10
ok kinda got it working... but not enough to view a decent image.

Ran this command

trent@trent-desktop:~$ vlc -- enable-v4l2 v4l2://devices/pci0000:00/0000:00:02.1/usb1/1-4/1-4:1.0/input/input6

which produced this in the console

```
VLC media player 0.9.8a Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.8a Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=x86_64-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu4' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-realrtsp' '--enable-x264' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=x86_64-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "en_GB"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.Debian  **
**  for more information.                     **
**                                            **
************************************************
libdvdread: Can't stat enable-v4l2
No such file or directory
libdvdnav: vm: failed to open/read the DVD
[00000415] access_directory access error: enable-v4l2: No such file or directory
[00000415] access_file access error: cannot open file enable-v4l2 (No such file or directory)
[00000409] main input error: open of `enable-v4l2' failed: could not create access: no suitable access module
[00000421] v4l2 demux error: cannot open video device (No such file or directory)
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM devices/pci0000
[00000421] v4l2 demux error: cannot open device devices/pci0000 for ALSA audio (No such file or directory)
[00000421] v4l2 demux error: cannot open device devices/pci0000 for OSS audio (No such file or directory)
libv4l2: error converting / decoding frame data: v4l-convert: error parsing JPEG header: Not a JPG file ?


[00000421] v4l2 demux error: Failed to wait (VIDIOC_DQBUF)
libv4l2: error converting / decoding frame data: v4l-convert: error parsing JPEG header: Bogus jpeg format


[00000421] v4l2 demux error: Failed to wait (VIDIOC_DQBUF)
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 4 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 2 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 2 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 4 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 2 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 8 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 4 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 2 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 2 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 4 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 5 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 2 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 6 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 5 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 4 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 2 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 5 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 4 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 4 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 2 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 4 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 2 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 2 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 5 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 4 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 2 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 9 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 2 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 7 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 2 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 2 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 4 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 2 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 2 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 2 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 4 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 4 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 2 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 2 more bits
libv4lconvert: Error decompressing JPEG: error: more then 63 AC components (67) in huffman unit
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 7 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 9 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 6 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 2 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 5 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 5 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 4 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 7 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 2 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 2 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 4 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 2 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 4 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 2 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 5 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 2 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 4 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 2 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 5 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 5 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 2 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 4 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 2 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 5 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 2 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 4 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 2 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 2 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 6 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 4 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 5 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 2 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 4 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 2 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 4 more bits

```

And the attached screenshot shows what i saw on the screen

---

### Post by allen.smith81 on 2009-04-13
No one any ideas?

---

