---
title: "Mic doesn't work on Ubuntu 10.04"
date: 2012-11-20
forum: Hardware
---

### Post by luxtux on 2012-11-20
Hi All,
I have a problem using the internal mic on Ubuntu 10.04. 
It doesn't work, and I haven't any idea about how to fix it.

I have only put these commands on terminal:

uname -a
Linux laptop 2.6.32-45-generic #100-Ubuntu SMP Wed Nov 14 10:41:11 UTC 2012 i686
 GNU Linux

aplay -l
**** Lista di PLAYBACK dispositivi hardware ****
scheda 0: Intel [HDA Intel], dispositivo 0: AD198x Analog [AD198x Analog]
 Sottoperiferiche: 1/1
 Sottoperiferica #0: subdevice #0

dpkg -l grep "alsa"
ii   [COLOR=#FF0000]alsa[/COLOR]-base                                          1.0.22.1+dfsg-0ubuntu3
                 ALSA driver configuration files
ii   [COLOR=#FF0000]alsa[/COLOR]-utils                                           1.0.22-0ubuntu5
                 ALSA utilities
ii   bluez-[COLOR=#FF0000]alsa[/COLOR]                                          4.0.60-0ubuntu8
                 Bluetooth audio support
ii   gstreamer0.10-[COLOR=#FF0000]alsa[/COLOR]                            0.10.28-1
                 GStreamer plugin for ALSA
ii   libesd-[COLOR=#FF0000]alsa[/COLOR]0                                       0.2.41-6ubuntu1
                 Enlightened Sound Daemon (ALSA)  -  transition
"c  libsdl1.2debian-[COLOR=#FF0000]alsa[/COLOR]                            1.2.13-4ubuntu4
                 Simple DirectMedia Layer (with X11 and ALSA
ii   libsox-fmt-[COLOR=#FF0000]alsa[/COLOR]                                   14.3.0-1.1build1
                 Sox[COLOR=#FF0000] alsa[/COLOR] format I/0 library

cat /proc/asound/card0/codec* | grep Codec 
Codec: Analog Devices AD1981 Codec: LSI ID 1040

Can you help me to understand where's the problem?
Thanks a lot

---

### Post by ajgreeny on 2012-11-20
Run ```
alsamixer
``` in terminal and check that the levels of outputs are not set too low or muted.
Move from slider to slider, and raise and lower levels with the cursor keys;
Mute and unmute with the "M" key.
Tab will move you from "playback" to "capture".
In capture page use spacebar to enable the different input devices (mic, line, CD, video).
Esc will save and exit.

Also you should make sure you have installed pulseaudio volume control (**pavucontrol**) and **padevchooser**, which I don't think are installed by default on 10.04.

---

### Post by luxtux on 2012-11-21
Hi [COLOR=Black][ajgreeny]("http://ubuntuforums.org/member.php?u=27747"),
thank you for answering.

**pavucontrol **and [/COLOR]**padevchooser **are installed.
I attach some screenshots at about alsamixer. You think the settings are ok?

---

### Post by ajgreeny on 2012-11-23
Sorry, I missed your reply.

However, I can not see anything in your screenshots that helps me figure out why your Mic is not working.

If  you scroll sideways in alsamixer is there an option for "mic select" as  shown in my screenshot?

---

### Post by luxtux on 2012-11-24
Hi,
the problem was solved. But I haven't an idea how.
Maybe, I haven't rebooted..
Thx

---

