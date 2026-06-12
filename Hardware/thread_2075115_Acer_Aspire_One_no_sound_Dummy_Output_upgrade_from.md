---
title: "Acer Aspire One no sound Dummy Output upgrade from 12.04 to 12.10"
date: 2012-10-23
forum: Hardware
---

### Post by kiswono on 2012-10-23
hi, i'm upgrading from 64-bit ubuntu 12.04 to 12.10
and i found that after upgrade my sound card not detected,
it only shows "Dummy Output" on "Sound Settings"

i'm using 
```
$ uname -a

Linux mycompname 3.5.0-18-generic #29-Ubuntu SMP Fri Oct 19 10:26:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

my laptop is Acer Aspire One 725

my alsa and pulseaudio package:
```
ii  alsa-base                                                   1.0.25+dfsg-0ubuntu3                              all          ALSA driver configuration files
ii  alsa-oss                                                    1.0.25-1                                          amd64        ALSA wrapper for OSS applications
ii  alsa-utils                                                  1.0.25-3ubuntu2                                   amd64        Utilities for configuring and using ALSA
ii  alsamixergui                                                0.9.0rc2-1-9.1                                    amd64        graphical soundcard mixer for ALSA soundcard driver
ii  bluez-alsa:amd64                                            4.101-0ubuntu6                                    amd64        Bluetooth ALSA support
ii  bluez-alsa:i386                                             4.101-0ubuntu6                                    i386         Bluetooth ALSA support
ii  gnome-alsamixer                                             0.9.7~cvs.20060916.ds.1-3                         amd64        ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa:amd64                                    0.10.36-1ubuntu1                                  amd64        GStreamer plugin for ALSA
ii  libsox-fmt-alsa                                             14.4.0-3                                          amd64        SoX alsa format I/O library
ii  xmms2-plugin-alsa                                           0.8+dfsg-4                                        amd64        XMMS2 - ALSA output
ii  gstreamer0.10-pulseaudio:amd64                              0.10.31-3ubuntu1                                  amd64        GStreamer plugin for PulseAudio
ii  gstreamer1.0-pulseaudio:amd64                               1.0.1-1                                           amd64        GStreamer plugin for PulseAudio
ii  libpulse-dev:amd64                                          1:2.1-0ubuntu4                                    amd64        PulseAudio client development headers and libraries
ii  libpulse-mainloop-glib0:amd64                               1:2.1-0ubuntu4                                    amd64        PulseAudio client libraries (glib support)
ii  libpulse-mainloop-glib0:i386                                1:2.1-0ubuntu4                                    i386         PulseAudio client libraries (glib support)
ii  libpulse0:amd64                                             1:2.1-0ubuntu4                                    amd64        PulseAudio client libraries
ii  libpulse0:i386                                              1:2.1-0ubuntu4                                    i386         PulseAudio client libraries
ii  libpulsedsp:amd64                                           1:2.1-0ubuntu4                                    amd64        PulseAudio OSS pre-load library
ii  libpulsedsp:i386                                            1:2.1-0ubuntu4                                    i386         PulseAudio OSS pre-load library
ii  libsox-fmt-pulse                                            14.4.0-3                                          amd64        SoX PulseAudio format I/O library
ii  pulseaudio                                                  1:2.1-0ubuntu4                                    amd64        PulseAudio sound server
ii  pulseaudio-esound-compat                                    1:2.1-0ubuntu4                                    amd64        PulseAudio ESD compatibility layer
ii  pulseaudio-module-gconf                                     1:2.1-0ubuntu4                                    amd64        GConf module for PulseAudio sound server
ii  pulseaudio-module-raop                                      1:2.1-0ubuntu4                                    amd64        RAOP module for PulseAudio sound server
ii  pulseaudio-module-x11                                       1:2.1-0ubuntu4                                    amd64        X11 module for PulseAudio sound server
ii  pulseaudio-module-zeroconf                                  1:2.1-0ubuntu4                                    amd64        Zeroconf module for PulseAudio sound server
ii  pulseaudio-utils                                            1:2.1-0ubuntu4                                    amd64        Command line tools for the PulseAudio sound server
ii  vlc-plugin-pulse                                            2.0.4-0ubuntu1                                    amd64        PulseAudio plugin for VLC

```

i have tried to purge alsa-base and pulseaudio then install again, reboot, but still not working..

i have tried to blacklist some module in /etc/modprobe.d/blacklist.conf, that i've read in archlinux forum is the cause of the similar problem, but no luck
```
# disable bluetooth
blacklist btusb

# possible soundcard bug
blacklist i82975x_edac

```

my sound card is
```
$ sudo lshw -c sound
  *-multimedia:0 UNCLAIMED
       description: Audio device
       product: Wrestler HDMI Audio [Radeon HD 6250/6310]
       vendor: Advanced Micro Devices [AMD] nee ATI
       physical id: 1.1
       bus info: pci@0000:00:01.1
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: latency=0
       resources: memory:90244000-90247fff
  *-multimedia:1 UNCLAIMED
       description: Audio device
       product: Hudson Azalia Controller
       vendor: Advanced Micro Devices [AMD]
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: latency=32
       resources: memory:90240000-90243fff

```

alsamixer output 
```
$ sudo alsamixer
cannot open mixer: No such file or directory

```

aplay output
```
$ sudo aplay -l
aplay: device_list:252: no soundcards found...

```

modinfo output
```
$ modinfo snd-hda-codec
filename:       /lib/modules/3.5.0-18-generic/kernel/sound/pci/hda/snd-hda-codec.ko
license:        GPL
description:    HDA codec core
srcversion:     88CD34C9956A915CBC37609
depends:        snd-pcm,snd,snd-hwdep
intree:         Y
vermagic:       3.5.0-18-generic SMP mod_unload modversions

```

is this kernel problem? and how to fix this?


btw somehow fglrx works worse than fglrx-updates for 12.10
but fglrx works better than fglrx-updates for 12.04 --> just sayin..

---

### Post by sddfdds on 2012-10-23
Yea, its a kernel problem...what kind of update would it be if you didnt have to deal with some ******** about your hardware not working anymore?  I have different hardware from you but still the same problem with snd-hda-intel and although its a half-assed fix, if you can roll back to a 3.2 kernel by holding shift when starting up, that'll fix your audio (but also knock you back to the stupid years old issue of suspend suddenly and randomly making your hard drive slow as death which is fixed in 3.5) so its something in between 3.2 and 3.5

---

### Post by kiswono on 2012-10-23
'____' ah i see.. thanks for your reply..

btw, some other failed attempt:
```

# alias snd-card-0 snd-hda-intel
#options snd-hda-intel model=laptop
#options snd-hda-intel model=auto
options snd-hda-intel model=acer-aspire position_fix=1

```

---

### Post by greyskulll on 2012-10-25
BUMP !!!

Got the exact same issue here ... practically clueless on fixing this ! :(

---

### Post by kiswono on 2012-10-25
yes, and when i choose to use older kernel from 12.04
```
Linux tribe 3.2.0-32-generic #51-Ubuntu SMP Wed Sep 26 21:33:09 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux                                                                                                                                                                       

```
my soundcard still not working.. >w<
it worked before when i still use 12.04..

---

### Post by kiswono on 2012-10-25
and still not working for newer kernel..
```
Linux tribe 3.6.3-030603-generic #201210211349 SMP Sun Oct 21 17:50:41 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by kiswono on 2012-10-29
the one and only, solution! yeah!!!

just add snd-hda-intel to /etc/modules
and restart, it works for linux-3.7 kernel ^^ 

source:

[https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit](https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit)

---

### Post by sddfdds on 2012-11-03
No luck for me unfortunately, with either the standard kernel or the current mainline

---

### Post by andrewlorien on 2013-09-08
The suggestion and link from kiswono worked for me, thanks!
that doc is a great walkthrough.  super-simple help in the appendices, straightforward steps in the main document.

It went wrong for me after a couple of months of uptime and a big system update.
uname -a
Linux radagast 3.2.0-53-generic #81-Ubuntu SMP Thu Aug 22 21:01:03 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

---

