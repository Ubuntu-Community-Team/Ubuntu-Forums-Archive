---
title: "Digital Audio Workstation (DAW) for Linux?"
date: 2009-04-02
forum: Installation &amp; Upgrades
---

### Post by nosman240 on 2009-04-02
I've been using Linux for a few months now and it's good stuff. I still have winXP on my machine though because I make music using FL Studio.  I was wondering if there are any good DAWs compatible with Linux? I looked into running FL in Wine but it had mixed reviews. Thanks for the input!

---

### Post by BrandonBan6 on 2009-04-02
Nosman, have you checked out any of the apps Ubuntu Studio uses? [http://ubuntustudio.org/](http://ubuntustudio.org/)

I haven't used it myself, but I've heard good things.

---

### Post by nosman240 on 2009-04-02
haven't heard of it. just checked it out though, and it looks really cool. the only thing is it's more of a hobby at the moment and i dont think i'd want to reinstall Ubuntu if i can avoid it. I'll definitely keep that in mind if i ever get more serious about it and more serious about disliking Windows :-P

---

### Post by BrandonBan6 on 2009-04-02
Well, you don't have to reinstall Ubuntu at all, just find out the audio packages it uses. [https://wiki.ubuntu.com/UbuntuStudio/PackageList](https://wiki.ubuntu.com/UbuntuStudio/PackageList)

All Ubuntustudio is, is ubuntu refined for a specific purpose. You can do the same thing, just install those packages onto your current ubuntu installation.

---

### Post by nosman240 on 2009-04-02
ah, i shouldve figured that one out on my own... :-P

i'll definitely look at some of this stuff if thats the case, thanks again for the help

---

### Post by BrandonBan6 on 2009-04-02
No problem! :) Good luck!

---

### Post by logos34 on 2009-04-02
Ardour is the Main DAW program in UbuntuStudio.  Rosegarden too (KDE app).

> $ apt-cache show ardour
Package: ardour
Priority: optional
Section: universe/sound
Installed-Size: 29860
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Debian Multimedia Team <debian-multimedia@lists.debian.org>
Architecture: amd64
Version: 1:2.3.1-1
Replaces: ardour-gtk
Depends: jackd (>= 0.103.0), libart-2.0-2 (>= 2.3.18), libasound2 (>> 1.0.14), libatk1.0-0 (>= 1.20.0), libc6 (>= 2.7-1), libcairo2 (>= 1.5.8), libfftw3-3, libgcc1 (>= 1:4.1.1-21), libglib2.0-0 (>= 2.15.5), libgnomecanvas2-0 (>= 2.11.1), libgtk2.0-0 (>= 2.12.0), libjack0 (>= 0.109.2), liblo0 (>= 0.23), liblrdf0, libpango1.0-0 (>= 1.19.3), libraptor1 (>= 1.4.16), libsamplerate0, libstdc++6 (>= 4.1.1-21), libxml2 (>= 2.6.27), libxslt1.1 (>= 1.1.20), python, python-gtk2, python-twisted
Recommends: www-browser | iceweasel
Suggests: jamin, qjackctl
Conflicts: ardour-gtk
Filename: pool/universe/a/ardour/ardour_2.3.1-1_amd64.deb
Size: 8733082
MD5sum: c3bfff20981c07cac23496eb03933fd9
SHA1: 0915fdbf379c77cd6dbe543cf52976ff5d9c901c
SHA256: 4c1589251bf8d139ea490c6ada5fd099b05816e6274768d3e819502cc1326ebc
Description: digital audio workstation (graphical gtk2 interface)
 Ardour is a multichannel hard disk recorder (HDR) and digital audio
 workstation (DAW).  It can be used to control, record, edit and run and
 complex audio setups.
 .
 Ardour supports pro-audio interfaces
 through the ALSA project, which provides high quality, well design
 device drivers and API's for audio I/O under Linux. Any interface
 supported by ALSA can be used with Ardour. This includes the
 all-digital 26 channel RME Hammerfall, the Midiman Delta 1010 and many
 others.
 .
 Ardour has support for 24 bit samples
 using floating point internally, non-linear editing with unlimited undo,
 a user-configurable mixer, MTC master/slave capabilities, MIDI hardware
 control surface compatibility.
 .
 It supports MIDI
 Machine Control, and so can be controlled from any MMC controller and
 many modern digital mixers.
 .
 Ardour contains a
 powerful multitrack audio editor/arranger that is completely
 non-destructive and capable of all standard non-linear editing
 operations (insert, replace, delete, move, trim, select,
 cut/copy/paste). The editor has unlimited undo/redo capacity and can
 save independent "versions" of a track or entire piece.
 .
 Ardour's editor supports the community-developed LADSPA
 plugin standard.  Arbitrary chains of plugins can be attached to any
 portion of a track.  Every mixer strip can have any number of inputs
 and outputs, not just mono, stereo or 5.1.  An N-way panner is
 included, with support for various panning models.  Pre- and post-fader
 sends exist, each with their own gain and pan controls.  Every mixer
 strip acts as its own bus, and thus the bus count in Ardour is
 unlimited.  You can submix any number of strips into another
 strip.
 .
 Ardour's channel capacity is limited only
 by the number on your audio interface and the ability of your disk
 subsystem to stream the data back and forth.
 .
 JACK
 (the JACK Audio Connection Kit) is used for all audio I/O, permitting
 data to be exchanged in perfect samplesync with other applications
 and/or hardware audio interfaces.
 .
 Ardour is
 sample rate and size neutral - any hardware formats from 8 to 32 bits,
 rates from 8kHz to 192kHz.  Internal processing in 32/64 bit IEEE
 floating point format.
 .
 Further information can be
 found at <http://ardour.org/>.
Homepage: [http://www.ardour.org/](http://www.ardour.org/)
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
  

---

