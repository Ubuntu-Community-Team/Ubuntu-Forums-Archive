---
title: "Why no modprobe.conf ? Then how to change via82xx DXS assumed boot setting?"
date: 2004-10-24
forum: Hardware &amp; Laptops
---

### Post by emperor on 2004-10-24
I thought 2.6.x kernels were suppose to use modprobe.conf file instead of modules.conf? But Instead there is a /etc/module.conf which appears to NOT be used based on what is in it! I am trying to get sound working with a Soyo KT600 that has the Via82xx chipset. I need to change the "assumed" DXS setting of 1 to another value, at least according to the documentation I found on the net. 

[http://www3.sympatico.ca/howlettfamily/epia/epia_howto/x310.html](http://www3.sympatico.ca/howlettfamily/epia/epia_howto/x310.html)

Section of interest:
============
in the recent driver version, a workaround is provided instead.
there is a module option "dxs_support", which defines how to handle
the DXS channels.  if you have a problem with the first pcm device,
try dxs_support=2 or dxs_support=3.

when dxs_support=2 is given, the DXS mode is disabled and you'll have
only the multi-channel playback mode.  this means, the chip is handled
as VIA8233A.  of course, you can play only on stream.  in this case,
dmix plugin would be a workaround.

when dxs_support=3 is given, only 48kHz is allowed for the DXS
channels.  that means, the sample-rate conversion will be done in
alsa-lib or OSS-emulation for playing MP3.  but it's cheaper than dmix
plugin.  so, try this once, and if still doesn't work, try the
previous one.
=============================================

During kernel boot I get this:
==================
via82xx: Assuming DXS channels with 48k fixed sample rate.
         Please try dxs_support=1 or dxs_support=4 option
         and report if it works on your machine.

So, someone is not sure what works and I need to try a few tweaks! 

So where do we add our tweaks, if no modules.conf! 

Anyone get sound working with a Via82

PS. is there a script file that runs last like RH's rc.local? If so, what would the name of that be?

---

### Post by im_ka on 2004-10-25
i have via onboard sound (via82xx) and it works without problems.

---

### Post by jdong on 2004-10-25
all the files inside /etc/modprobe.d comprise modprobe.conf. Stick it in any one you want, then run  **update-modules**.

---

### Post by jdong on 2004-10-25
[QUOTE=emperor]I thought 2.6.x kernels were suppose to use modprobe.conf file instead of modules.conf? But Instead there is a /etc/module.conf which appears to NOT be used based on what is in it! I am trying to get sound working with a Soyo KT600 that has the Via82xx chipset. I need to change the "assumed" DXS setting of 1 to another value, at least according to the documentation I found on the net. 

[http://www3.sympatico.ca/howlettfamily/epia/epia_howto/x310.html](http://www3.sympatico.ca/howlettfamily/epia/epia_howto/x310.html)

Section of interest:
============
in the recent driver version, a workaround is provided instead.
there is a module option "dxs_support", which defines how to handle
the DXS channels.  if you have a problem with the first pcm device,
try dxs_support=2 or dxs_support=3.

when dxs_support=2 is given, the DXS mode is disabled and you'll have
only the multi-channel playback mode.  this means, the chip is handled
as VIA8233A.  of course, you can play only on stream.  in this case,
dmix plugin would be a workaround.

when dxs_support=3 is given, only 48kHz is allowed for the DXS
channels.  that means, the sample-rate conversion will be done in
alsa-lib or OSS-emulation for playing MP3.  but it's cheaper than dmix
plugin.  so, try this once, and if still doesn't work, try the
previous one.
=============================================

During kernel boot I get this:
==================
via82xx: Assuming DXS channels with 48k fixed sample rate.
         Please try dxs_support=1 or dxs_support=4 option
         and report if it works on your machine.

So, someone is not sure what works and I need to try a few tweaks! 

So where do we add our tweaks, if no modules.conf! 

Anyone get sound working with a Via82

PS. is there a script file that runs last like RH's rc.local? If so, what would the name of that be?[/QUOTE]
 oh yeah, Debian uses /etc/init.d/bootmisc.sh

---

### Post by emperor on 2004-10-25
[QUOTE=im_ka]i have via onboard sound (via82xx) and it works without problems.[/QUOTE]
when you type "dmesg" in a terminal, do you see this statement:
========================================
via82xx: Assuming DXS channels with 48k fixed sample rate.
Please try dxs_support=1 or dxs_support=4 option
and report if it works on your machine.

I have on/off like sound on the OSS PCM slider only, very wierd!

---

### Post by emperor on 2004-10-25
My chipset is the via8237, it looks this may be the problem. There is a patch in the 2.6.10.rc1 kernel.


ChangeSet 2004/10/20 14:12:54+02:00, perex @ suse.cz [diffview]
[ALSA] Add VIA8237 driver type

VIA82xx driver
VIA8237 and later chips are handled as a different type from VIA8233,
since they don't support the AC97 slot mapping any more.
The alsa-lib will resolve the 5.1 remapping for them.

Signed-off-by: Takashi Iwai <tiwai@suse.de>

---

### Post by FLeiXiuS on 2004-10-25
Take a look at 

```
/etc/modutils/alias
```

---

### Post by emperor on 2004-10-26
I need a straight answer from someone who knows how this system is configured. The Debian documentation is out of date as well. The Debian doc says the sound options goes in the "conf.modules"; yea right! I think that module.conf and modutils is obsolute with 2.6 series kernels. So who around here knows "what" about "how" and "where"! I am about to either go buy another sound card or blow Ubuntu off this drive. I need a straight answer from someone who "really" knows! Where do module option settings go! It should not be a mystery or a guessing game!

---

### Post by jdong on 2004-10-26
patience. Debian still uses /etc/modules/ to house all module  configurations. There's where all the config goes. If it's a **module-init-tools specific** command (like load or unload actions), they need to go in /etc/modprobe.d/. After editing, you must run **update-modules** for your changes to be merged with the system modules config.

---

### Post by emperor on 2004-10-28
I added my options to "alsa-base" but they had no effect on the snd-via82xx configuration. The lines I added did show up in modules.conf after running module-update. I rebooted the machine and no change in behavior or indication that the  changes were applied in dmesg log.

Coming from Fedora, hardware changes are not a big issue because Fedora auto-detects removal and addition of hardware.  In Archlinux, you just edit "rc.conf" and that's pretty easy too.  How do I do this in Ubuntu (Debian) with a 2.6 kernel?

Next I need to unload the current sound drivers in Ubuntu, disable the on-board sound, install a "SB live" card and then alter Ubuntu to load the associated driver(s).

---

### Post by emperor on 2004-10-30
I disabled the oinboard via8237 sound and installed a SB Live card. Upon a reboot Ubuntu's 2.6 kernel found the new hardware automaticly and sound now works properly. I believe the problem with the via8237 support is a kernel problem and should be fixed in a a future 2.6.10 or above kernel release.[img]http://www.ubuntuforums.org/images/smilies/eusa_dance.gif[/img]

---

### Post by MaZiNgA on 2004-11-11
I'm still looking for the solution of this problem... :( 
Anyone?

---

### Post by emperor on 2004-11-18
"man modprobe.d" says the options go in a file in the /etc/modprobe.d directory using the "option" key word. I believe you can create a new file in the modprobe.d directory or put it in one of the existing files, like "alsa-base". As I understand it, the following would be the proper entry format:
 
 option  via8237 (then list any valid options here)
 
 Give this a try and let us know if it works for you!
 
 I ended up installing an old SBLive card in the problem machine, this was before I had read about the method above.

---

### Post by taygan on 2005-01-10
I'm running hoary with the 2.6.10 kernel and an ASUS a7v600-x motherboard with via8237 onboard sound.

Replacing the kernel did not fix my poor GStreamer and system sounds (way too much bass stutter), but adding this line to /etc/modprobe.d/alsa-base worked wonders (you can add the line to any file in the /etc/modprobe.d folder)

```

options snd_via82xx dxs_support=4

```

options snd_via82xx dxs_support=1   - worked almost as well.
options snd_via82xx dxs_support=2   - froze xmms
options snd_via82xx dxs_support=3   - poor GStreamer and system sounds


this website helped a lot: [http://alsa.opensrc.org/index.php?page=via8233](http://alsa.opensrc.org/index.php?page=via8233)

an excerpt explaining dxs_support settings:

#  0 - the default value; set 48000 Hz only mode in most cases, except on some known motherboards (which are in the whitelist).
# 1 - enable full DXS support (at any supported sample rate).
# 2 - disable DXS support completely. In this case the hardware mixing ability of the chip is not used.
# 3 - use DXS at 48000 Hz only.
# 4 - enable DXS at any supported sample rate, but always set the codec to 48000 Hz (apparently on some motherboards this works better than dxs_support=1).

---

### Post by Robodoc on 2005-05-27
I have or better - thank you!  - had the same problem for months: no sound at all. 
Playing with alsamixer solved the problem at least parly.

I had to change "Rear Jac" in alsamixer to "Front Ou", to hear anything at all; play with some other settings, set the first VIA DXS-Setting to about 80%, and now I have sounds in some quality.

So I'll try to tune it up right now.

My question is:
Where do I have add  "options snd_via82xx dxs_support=4"?
Add it just anywhere in a file auf /etc/modprobe.d, e.g. at the end of the file?

Thank you, you helped a lot!
 \\:D/

---

### Post by eggdeng on 2006-11-01
If there is anyone still alive who has this problem, one solution is to insert the line 

options snd-via82xx dxs_support=3 

in /etc/modprobe.d/alsa-base and just reboot.8)

---

