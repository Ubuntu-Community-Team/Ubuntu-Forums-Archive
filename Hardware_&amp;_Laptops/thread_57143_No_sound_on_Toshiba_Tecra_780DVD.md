---
title: "No sound on Toshiba Tecra 780DVD"
date: 2005-08-15
forum: Hardware &amp; Laptops
---

### Post by zorglub on 2005-08-15
Hi !

I recently installed Warty on my old Tecra 780DVD. Everything worked fine except that the build in soundcard is not recognized.

Specifications:

The sound system chipset is Yamaha OPL3-SA3.
Sound formats supported : SoundBlaster Pro v 3.01, MIDI, Windows Sound System v 2.0
16 bit stereo audio playback/record supported with 48kHz maximum samplig rate
Synthesis Policy: FM synthesis with Wavetable software support
Fulle duplex function including simultaneous playback and record.

Originally the laptop was running with W95 and all worked fine...... but I cannot stand this OS anymore.... so I decided to migrate to Ubuntu.  I also tried to install Hoary 5.04 but had to give up because display problems in 1024x768 mode.

I previously tried to follow the instruction posted some time ago by a forum member called "Fred_og_ro" in answer to "bikeboy" but I don't have any /etc/modules.conf and /etc/modules configuration files to edit.

I'm a newbie to Ubuntu and after spending 3 days nearly non stop digging for some info about this problem i'm close to give up  ](*,) 

Any suggestion will be highly appreciated !!
Thanks in advance !

---------------------------------------------------------------------------------------------

OK the problem is solved  :-P 

1) Reinstalled Ubuntu 5.04 Hoary from scratch

2) Used a VESA driver instead of the S3 virge MX and edited manually etc/X11/xorg.conf to add the "1024x768" resolution => ok

3) Used info provided by the following thread :

[http://ubuntuforums.org/showthread.php?t=32651](http://ubuntuforums.org/showthread.php?t=32651)

4) Thanks dbott67  :razz:

---

