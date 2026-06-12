---
title: "No sound after yesterday update"
date: 2008-08-03
forum: Hardware
---

### Post by clains on 2008-08-03
Hello. 
It's my first post on this forum so, Hi Everybody :) 

First post, and first problem. 
After yesterday update, my system [ ubuntu 8.04 ] can't find sound card :/ 
I have Acer Extensa 5220 laptop. 
```
sade@sade-desk:~$ aplay -l
aplay: device_list:205: nie znaleziono &#380;adnych kart d&#378;wi&#281;kowych...
sade@sade-desk:~$ dpkg -l | grep gstreamer
ii  gstreamer0.10-alsa                         0.10.18-3                                                  GStreamer plugin for ALSA
ii  gstreamer0.10-esd                          0.10.7-3ubuntu0.1                                          GStreamer plugin for ESD
ii  gstreamer0.10-ffmpeg                       0.10.3-6                                                   FFmpeg plugin for GStreamer
ii  gstreamer0.10-fluendo-mp3                  0.10.7.debian-1                                            Fluendo mp3 decoder GStreamer plugin
ii  gstreamer0.10-fluendo-mpegdemux            0.10.15-1                                                  GStreamer plugin for demuxing of MPEG2 strea
ii  gstreamer0.10-fluendo-mpegmux              0.10.2-1                                                   GStreamer plugin for muxing of MPEG2 TS stre
ii  gstreamer0.10-gnomevfs                     0.10.18-3                                                  GStreamer plugin for GnomeVFS
ii  gstreamer0.10-gnonlin                      0.10.9-1                                                   non-linear editing module for GStreamer
ii  gstreamer0.10-pitfdll                      0.9.1.1+cvs20080215-1                                      GStreamer plugin for using MS Windows binary
ii  gstreamer0.10-plugins-bad                  0.10.6-5                                                   GStreamer plugins from the "bad" set
ii  gstreamer0.10-plugins-bad-multiverse       0.10.6-1                                                   GStreamer plugins from the "bad" set (Multiv
ii  gstreamer0.10-plugins-base                 0.10.18-3                                                  GStreamer plugins from the "base" set
ii  gstreamer0.10-plugins-base-apps            0.10.18-3                                                  GStreamer helper programs from the "base" se
ii  gstreamer0.10-plugins-farsight             0.12.5-2ubuntu1                                            plugins for Gstreamer for Audio/Video confer
ii  gstreamer0.10-plugins-good                 0.10.7-3ubuntu0.1                                          GStreamer plugins from the "good" set
ii  gstreamer0.10-plugins-ugly                 0.10.7-3ubuntu1                                            GStreamer plugins from the "ugly" set
ii  gstreamer0.10-plugins-ugly-multiverse      0.10.7-1                                                   GStreamer plugins from the "ugly" set (Multi
ii  gstreamer0.10-pulseaudio                   0.9.7-2                                                    GStreamer plugin for PulseAudio
ii  gstreamer0.10-schroedinger                 1.0.1-2                                                    GStreamer plugin for encoding/decoding of Di
ii  gstreamer0.10-sdl                          0.10.6-5                                                   GStreamer plugin for SDL output
ii  gstreamer0.10-tools                        0.10.18-4ubuntu1                                           Tools for use with GStreamer
ii  gstreamer0.10-x                            0.10.18-3                                                  GStreamer plugins for X11 and Pango
ii  libgstreamer-plugins-base0.10-0            0.10.18-3                                                  GStreamer libraries from the "base" set
ii  libgstreamer0.10-0                         0.10.18-4ubuntu1                                           Core GStreamer libraries and elements
ii  totem-gstreamer                            2.22.1-0ubuntu2                                            A simple media player for the Gnome desktop 
sade@sade-desk:~$
```

But, when i switch to another kernel [ i thik it is another kernel - i choose  2.6.24-19-generic from GRUB ] the sound is back, and system can find a sound card :
```
sade@sade-desk:~$ aplay -l
**** Lista PLAYBACK urz&#261;dze&#324; ****
karta 0: Intel [HDA Intel], urz&#261;dzenie 0: ALC268 Analog [ALC268 Analog]
  Urz&#261;dzenia podrz&#281;dne: 1/1
```
Is anybody having this problem or just me ? 

Ps. Sorry for my english :)

---

### Post by Crosbie on 2008-08-04
I have a similar problem.  Latest version is reporting no sound card or gstreamer plugins.  This is on a desktop however.

---

