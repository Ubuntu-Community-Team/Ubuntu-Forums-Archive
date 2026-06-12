---
title: "hoontech dsp24 + adc dac 2000"
date: 2009-08-03
forum: Hardware
---

### Post by slafille on 2009-08-03
hello,
i have a probleme with jack and my soundcard hoontech dsp24+adc dac 2000 rack.
jack start and stop immediately
 
here are the messages from jack
 
21:44:11.869 Patchbay deactivated.
21:44:12.006 Statistics reset.
21:44:12.080 ALSA connection graph
 
change.
 
21:44:12.233 ALSA connection change.
 
21:44:13.535 Startup script...
 
21:44:13.536 artsshell -q terminate
 
21:44:14.328 Startup script terminated with exit status=256.
 
21:44:14.329 JACK is starting...
 
21:44:14.330 /usr/bin/jackd -R -dalsa -r44100 -p128 -n3 -D -Chw:0 -Phw:0 -i8 -o8
 
21:44:14.335 JACK was started with PID=5501.
 
jackd 0.109.2
 
Copyright 2001-2005 Paul Davis and others.
 
jackd comes with ABSOLUTELY NO WARRANTY
 
This is free software, and you are welcome to redistribute it
 
under certain conditions; see the file COPYING for details
 
JACK compiled with System V SHM support.
loading driver ..
 
apparent rate = 44100
 
creating alsa driver ... hw:0|hw:0|128|3|44100|8|8|nomon|swmeter|-|32bit
 
control device hw:0
 
control open "hw:0" (No such file or directory)
 
ALSA lib pcm_hw.c:1207:(_snd_pcm_hw_open) Invalid value for card
 
ALSA lib pcm_hw.c:1207:(_snd_pcm_hw_open) Invalid value for card
 
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
 
cannot load driver module alsa
no message buffer overruns
 
21:44:14.469 JACK was stopped successfully.
21:44:14.470 Post-shutdown script...
 
21:44:14.471 killall jackd
 
21:44:14.558 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect
 
to server. Please check the messages window for more info.
 
jackd: aucun processus tuÃ©
21:44:16.191 Post-shutdown script terminated with exit status=256.
 
 
Please help me, I'm a beginner on linux ! i don't want to come back to windows!

---

