---
title: "microphone will not work"
date: 2017-06-25
forum: Hardware
---

### Post by jgw on 2017-06-25
I have been trying to get a microphone to work.  I have installed one plugged into the microphone connector on the back of the pc and I also have one included in my c525 logictech webcam.  I have failed with both and thought to post this before I REALLY screw things up.  In my quest I was kinda getting sound out of the one connected to the back of my machine but even that is now giving me nothing.  I have included two files (below) on pastebin in an effort to tell whoever just what I have and what I have done.  I didn't, for instance, have pulse audio installed so I installed it (it is still not starting when turning on or rebooting but I can fix that I think.  What I am really wondering is I should have installed it in the first place).  

This file shows what I have done in the terminal
[https://pastebin.com/T6ftCrq5](https://pastebin.com/T6ftCrq5)

this file shows the results of alsamixer (and I wonder why it does not show the rear microphone connection)
[https://pastebin.com/dDyfFXQS](https://pastebin.com/dDyfFXQS)

Thoughts?

---

### Post by howefield on 2017-06-25
Thread moved to the "*Hardware*" forum.

---

### Post by efflandt on 2017-06-26
Did you try hitting F4 in alsamixer and see what that shows?```
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; AlsaMixer v1.1.2 &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: HDA Intel MID                                  F1:  Help               &#9474;
&#9474; Chip: Realtek ALC887                                 F2:  System information &#9474;
&#9474; View: F3: Playback  F4:[Capture] F5: All             F6:  Select sound card  &#9474;
&#9474; Item: Front Mic Boost [dB gain: 0.00, 0.00]          Esc: Exit               &#9474;
&#9474;                                                                              &#9474;
&#9474;    &#9484;&#9472;&#9472;&#9488;       &#9484;&#9472;&#9472;&#9488;       &#9484;&#9472;&#9472;&#9488;       &#9484;&#9472;&#9472;&#9488;                             &#9484;&#9472;&#9472;&#9488;    &#9474;
&#9474;    &#9474;  &#9474;       &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;                             &#9474;  &#9474;    &#9474;
&#9474;    &#9474;  &#9474;       &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;                             &#9474;  &#9474;    &#9474;
&#9474;    &#9474;  &#9474;       &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;                             &#9474;  &#9474;    &#9474;
&#9474;    &#9474;  &#9474;       &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;                             &#9474;  &#9474;    &#9474;
&#9474;    &#9474;  &#9474;       &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;                             &#9474;  &#9474;    &#9474;
&#9474;    &#9474;  &#9474;       &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;                             &#9474;  &#9474;    &#9474;
&#9474;    &#9474;  &#9474;       &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;                             &#9474;  &#9474;    &#9474;
&#9474;    &#9474;  &#9474;       &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;                             &#9474;  &#9474;    &#9474;
&#9474;    &#9474;  &#9474;       &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;                             &#9474;  &#9474;    &#9474;
&#9474;    &#9474;  &#9474;       &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;                             &#9474;  &#9474;    &#9474;
&#9474;    &#9474;  &#9474;       &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;                             &#9474;  &#9474;    &#9474;
&#9474;    &#9492;&#9472;&#9472;&#9496;       &#9492;&#9472;&#9472;&#9496;      L&#9492;&#9472;&#9472;&#9496;R      &#9492;&#9472;&#9472;&#9496;    Front Mic  Front Mic     &#9492;&#9472;&#9472;&#9496;    &#9474;
&#9474;                        CAPTURE    -------                                    &#9474;
&#9474;    0<>0       0<>0     100<>100     0<>0                             0<>0    &#9474;
&#9474;<Front Mic >Line Boost  Capture   Capture 1  Input Sour Input Sour Rear Mic B &#9474;
&#9474;                                                                              &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;
```I seem to remember my microphone only working briefly when plugged in, then ending up grayed out in sound settings, and not working in steam. I know that installing "pavucontrol" helped, but I do not remember if merely installing that resolved it or if I had to do anything with it.

---

### Post by Bucky Ball on 2017-06-26
> **efflandt said:**
> I know that installing "pavucontrol" helped, but I do not remember if merely installing that resolved it or if I had to do anything with it.

+1. Install Pulseaudio Volume Control from the repositories, launch that, get some music/sound going and check the Playback tab. Is the level meter moving? If not, check the Input Devices tab and make sure you have the correct device selected in the 'Port' drop-down menu. Check the Output Devices tab and do the same.

Sometimes needs a bit of experimentation, but if you're getting the levels bouncing that is a good sign.

---

### Post by jgw on 2017-06-26
I have now cleverly screwed things up.  Pulsaudio volume tells me that I no longer have any devices and only a dummy output.  cat /proc/asound/cards gets me:
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xf9ff4000 irq 16
 1 [C525           ]: USB-Audio - HD Webcam C525
                      HD Webcam C525 at usb-0000:03:00.0-3.4, full speed

greg@greg:~$ pulseaudio --dump-conf get me:

### Read from configuration file: /etc/pulse/daemon.conf ###
daemonize = no
fail = yes
high-priority = yes
nice-level = -11
realtime-scheduling = yes
realtime-priority = 5
allow-module-loading = yes
allow-exit = yes
use-pid-file = yes
system-instance = no
local-server-type = user
cpu-limit = no
enable-shm = yes
flat-volumes = no
lock-memory = no
exit-idle-time = 20
scache-idle-time = 20
dl-search-path = /usr/lib/pulse-8.0/modules
default-script-file = /etc/pulse/default.pa
load-default-script-file = yes
log-target = 
log-level = notice
resample-method = auto
enable-remixing = yes
enable-lfe-remixing = yes
lfe-crossover-freq = 120
default-sample-format = s16le
default-sample-rate = 44100
alternate-sample-rate = 48000
default-sample-channels = 2
default-channel-map = front-left,front-right
default-fragments = 4
default-fragment-size-msec = 25
enable-deferred-volume = yes
deferred-volume-safety-margin-usec = 1
deferred-volume-extra-delay-usec = 0
shm-size-bytes = 0
log-meta = no
log-time = no
log-backtrace = 0
rlimit-fsize = -1
rlimit-data = -1
rlimit-stack = -1
rlimit-core = -1
rlimit-rss = -1
rlimit-as = -1
rlimit-nproc = -1
rlimit-nofile = 256
rlimit-memlock = -1
rlimit-locks = -1
rlimit-sigpending = -1
rlimit-msgqueue = -1
rlimit-nice = 31
rlimit-rtprio = 9
rlimit-rttime = 200000

Alsamixer f4 gets me:
[IMG]~/home/greg/Pictures/screenshot from 2017-06-26 11-39-51.jpg[/IMG]


Here is what I did to get to this point:
=> Purge alsa-base and pulseaudio, eg:
sudo apt-get remove --purge alsa-base
sudo apt-get remove --purge pulseaudio
sudo apt-get install alsa-base
sudo apt-get install pulseaudio
sudo alsa force-reload
reboot

Oh - and I have audacious playing music for me with no problem (currently playing Annie Ross - Love for Sale <g>).  So, pulsaudio tells that I have no devices and music is playing.  
OH - I also no longer have a sound icon in the top menu bar.  To fix that I tried: ~$ sudo apt install --reinstall indicator-sound
which didn't get me any sound icon.

---

### Post by jgw on 2017-06-27
I now am back where I started.  The microphone works, if I am about .5" away from it.  Any further and its like I am speaking into a tunnel.  I used to be able to just talk and it picked it up.  I also turned off one speaker output (there are 2, left and right) to see if that made any difference - it didn't.  I also cannot see the camera microphone in the pulseaudio volume control although it is there:
greg@greg:~$ cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xf9ff4000 irq 16
 1 [C525           ]: USB-Audio - HD Webcam C525
                      HD Webcam C525 at usb-0000:03:00.0-3.4, full speed

I should probably also report that, in pulseaudio volume control/configuration tab, it must be set to analog stereo duplex is the only setting which will show the microphone.  If I try analog stereo output the microphone goes away.  

This is not an unknown problem as I read a pile of threads on this one.  Everybody eventually seems to overcome but I have failed miserably.  When I start 'fixing' stuff I tend to screw things up mightily so I thought I would ask if anybody has a solution or this is just something to live with.  Oh, my sound icon has now magically appeared again (part of the magic of computers).  Audacious currently playing peggy lee singing fever.
Thank you..................

---

