---
title: "streaming audio"
date: 2004-12-30
forum: General Help
---

### Post by liquid boy on 2004-12-30
um, i'm trying to find a way to listen to music on this site
[www.mp3.com.au/thedry](www.mp3.com.au/thedry)
i tried to use mplayer, but apparently it doesnt work with warty (what i'm using) or something.
is there another option other than mplayer to play asx files? (or is it mp3's streamed via asx... what ever it is...)

---

### Post by macewan on 2004-12-30
[http://www1.mplayerhq.hu/MPlayer/releases/codecs/](http://www1.mplayerhq.hu/MPlayer/releases/codecs/)

or

[ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat)
testing
main

[https://www.ubuntulinux.org/wiki/RestrictedFormats](https://www.ubuntulinux.org/wiki/RestrictedFormats)

mplayer-586
mplayer-fonts
mozilla-mplayer
mplayer-doc (optional)
w32codecs

---

### Post by liquid boy on 2004-12-30
hmm, when i try to install mplayer586 i an error that it couldnt mark for instillation:


mplayer-586:
  Depends: libartsc0 (>=1.3.1) but 1.2.3-1 is to be installed
  Depends: libfribidi0 (>=0.10.4-5) but 0.10.4-3 is to be installed
  Depends: libggi2 (>=1:2.0.5) but 1:2.0.4-3 is to be installed
  Depends: libpng12-0 (>=1.2.8rel) but 1.2.5.0-7ubuntu1 is to be installed
  Depends: libungif4g (>=4.1.3) but 4.1.0b1-6 is to be installed

---

### Post by liquid boy on 2004-12-30
> [http://www1.mplayerhq.hu/MPlayer/releases/codecs/](http://www1.mplayerhq.hu/MPlayer/releases/codecs/)
but i need mplayer to acutally go before i download codecs. the problem is that the only mplayer that synaptic will let me install (mplayer - custom) doesnt work (i click the icon in the apps menu, and nothing happens.)

> 
[ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat)
testing
main
yep, i've already got that.

> 
[https://www.ubuntulinux.org/wiki/RestrictedFormats](https://www.ubuntulinux.org/wiki/RestrictedFormats)

mplayer-586
mplayer-fonts
mozilla-mplayer
mplayer-doc (optional)
w32codecs


when i try to install mplayer 586 it tells me it can't install:

> mplayer-586:
  Depends: libartsc0 (>=1.3.1) but 1.2.3-1 is to be installed
  Depends: libfribidi0 (>=0.10.4-5) but 0.10.4-3 is to be installed
  Depends: libggi2 (>=1:2.0.5) but 1:2.0.4-3 is to be installed
  Depends: libpng12-0 (>=1.2.8rel) but 1.2.5.0-7ubuntu1 is to be installed
  Depends: libungif4g (>=4.1.3) but 4.1.0b1-6 is to be installed

---

### Post by macewan on 2005-01-04
[QUOTE=liquid boy]but i need mplayer to acutally go before i download codecs. [/QUOTE]


nah, I use xine with the codecs - works fine. give it a try.

---

### Post by fng on 2005-01-04
mplayer from the marillat repository is broken for ubuntu :(

---

### Post by jbh on 2005-01-04
There's a thread somewhere "Multimedia Ubunto How-To" where some guy compiled Mplayer. I had to compile Mplayer in a 32bit chroot to get it to work.

---

### Post by macewan on 2005-01-04
[http://gmms.sourceforge.net/](http://gmms.sourceforge.net/)

might help in the mean time

-----------------------------------
-----------------------------------
-----------------------------------

hrm, got it working with gxine, so it is possible

give it a try  8-) 

[http://www.macewan.org/screenshots/thedry.jpg](http://www.macewan.org/screenshots/thedry.jpg)

---

