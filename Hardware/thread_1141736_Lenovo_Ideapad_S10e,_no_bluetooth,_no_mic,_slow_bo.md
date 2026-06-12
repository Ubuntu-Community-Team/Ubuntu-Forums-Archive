---
title: "Lenovo Ideapad S10e, no bluetooth, no mic, slow boot"
date: 2009-04-28
forum: Hardware
---

### Post by liborw on 2009-04-28
Hello, 
I have just installed Ubuntu 9.04 on mi Ideapad S10e, I have red that everything should work, but not in mi case. 

First I can't make bluetooth working, Fn+F5 have no affect and hardware button just switch on/off wifi.

Mic also don't work.

And loading of GRUM takes abut 30sec.

Thanks for help.

---

### Post by Obi Wan Tin on 2009-04-29
Hi liborw,

I've tried Ubuntu 9.04 (UNR version) on two different types of S10e. First on one, with 4GB SSD disk with preinstaled windows XP and I also found loading grub excrutiently long. Now I have one without the SSD disk and it's loaded almost in no time. Longer loading time is, by my opinion, caused with some issues with SSD disk.

My bloototh work fine, but I confirm the other complains: I've spent some time getting microphone work, but with no succes. Fn+F5 combination doesn work neither, but to be honest, I have no idea what should it do - turning off wifi with just hardware switch is good enough for me.

I know i didn't help at all, but at least you knoe you're not alone.

P.S. I assume, you meant GRUB not GRUM

---

### Post by Obi Wan Tin on 2009-04-29
A peace of update. I've just found this post:

[http://ubuntuforums.org/showpost.php?p=7162344&postcount=222]("http://ubuntuforums.org/showpost.php?p=7162344&postcount=222")

I hope it helps.

(this is link to whole thread:
[http://ubuntuforums.org/showthread.php?t=1046137&highlight=S10e&page=23]("http://ubuntuforums.org/showthread.php?t=1046137&highlight=S10e&page=23")
)

---

### Post by liborw on 2009-04-29
Hi, 
Sure, GRUM is GRUB and I have also the SSD version of S10e, but unfortunately getting one without SSD is not an option for me. Is ther a way how to remove the SSD or disable it? I dont use it any way. 

I'm suspicious that bluetooth is on (led is blue and purple) when I switch S10e on but after while it goes off (led is just blue).

Another thing is not really problem but little strange, I'm connected to wifi but iwconfig shows Not-Associated.
 
Thanks for the help with mic.

---

### Post by mr.menace on 2009-05-19
Hi. Just wanted to bump your thread. I have the exact same problems as you describe, on my S10e. Has SSD 4gb and a SATA 160gb. I thought having / on the ssd and /home and /usr both on the sata would make booting quick, but it's quite slow. GRUB loads slow.

$ uname -a:
Linux microbe 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

No working mic (going to try the tip added here), no bluetooth, even though listed in dmesg like this:
<pre>
$ dmesg | grep -i blu
[    0.720039] Bluetooth: Core ver 2.13
[    0.720108] Bluetooth: HCI device and connection manager initialized
[    0.720108] Bluetooth: HCI socket layer initialized
[   11.800693] Bluetooth: L2CAP ver 2.11
[   11.800697] Bluetooth: L2CAP socket layer initialized
[   11.800703] Bluetooth: SCO (Voice Link) ver 0.6
[   11.800706] Bluetooth: SCO socket layer initialized
[   11.800790] Bluetooth: RFCOMM socket layer initialized
[   11.800805] Bluetooth: RFCOMM TTY layer initialized
[   11.800809] Bluetooth: RFCOMM ver 1.10
[   25.944099] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   25.944109] Bluetooth: BNEP filters: protocol multicast

cam don't work, but it seems video playback also fails when i try to playback a random mpeg off the net:

$ vlc Desktop/DELTA.MPG 
VLC media player 0.9.9a Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.9a Grishenko - (c) 1996-2009 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintainer-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=2ubuntu1' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-realrtsp' '--disable-dv' '--enable-x264' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[????????] x11 video output error: X11 request 132.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  132 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  80
  Current serial number in output stream:  81

strangely concurrent with errors from cheese:

$ cheese
The program 'cheese' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 70 error_code 11 request_code 132 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


Anyone got any ideas?

---

