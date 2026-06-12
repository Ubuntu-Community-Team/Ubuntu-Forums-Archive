---
title: "M-audio Fast Track and Ubuntu 10.04 ---JACK"
date: 2010-10-07
forum: Hardware
---

### Post by dogbin on 2010-10-07
Ok so I am trying to get my M-audio fast track working with Ubuntu 10.04, specifically Jack, and ardour. I set the settings on Jack to use my fast track usb device and I get the following output on the message screen.

p, li { white-space: pre-wrap; } [COLOR=#999999]10:31:18.290 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]10:31:18.403 Statistics reset.[/COLOR]
 [COLOR=#66cc99]10:31:18.415 ALSA connection graph change.[/COLOR]
 [COLOR=#cccc99]10:31:18.613 ALSA connection change.[/COLOR]
 [COLOR=#999999]10:31:28.387 Startup script...[/COLOR]
 [COLOR=#990099]10:31:28.388 artsshell -q terminate[/COLOR]
 [COLOR=#999999]sh: artsshell: not found[/COLOR]
 [COLOR=#999999]10:31:28.789 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]10:31:28.789 JACK is starting...[/COLOR]
 [COLOR=#990099]10:31:28.789 /usr/bin/jackd -dalsa -r44100 -p1024 -n2 -D -Chw:1 -Phw:1,0 -i2 -o2[/COLOR]
 [COLOR=#999999]10:31:28.791 JACK was started with PID=2339.[/COLOR]
 [COLOR=#999999]jackd 0.118.0[/COLOR]
 [COLOR=#999999]Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.[/COLOR]
 [COLOR=#999999]jackd comes with ABSOLUTELY NO WARRANTY[/COLOR]
 [COLOR=#999999]This is free software, and you are welcome to redistribute it[/COLOR]
 [COLOR=#999999]under certain conditions; see the file COPYING for details[/COLOR]
 [COLOR=#999999]Memory locking is unlimited - this is dangerous. You should probably alter the line:[/COLOR]
 [COLOR=#999999]     @audio   -  memlock    unlimited[/COLOR]
 [COLOR=#999999]in your /etc/limits.conf to read:[/COLOR]
 [COLOR=#999999]     @audio   -  memlock    1436520[/COLOR]
 [COLOR=#999999]no message buffer overruns[/COLOR]
 [COLOR=#999999]JACK compiled with System V SHM support.[/COLOR]
 [COLOR=#999999]loading driver ..[/COLOR]
 [COLOR=#999999]SSE2 detected[/COLOR]
 [COLOR=#999999]apparent rate = 44100[/COLOR]
 [COLOR=#999999]creating alsa driver ... hw:1,0|hw:1|1024|2|44100|2|2|nomon|swmeter|-|32bit[/COLOR]
 [COLOR=#999999]control device hw:1[/COLOR]
 [COLOR=#999999]configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods[/COLOR]
 [COLOR=#999999]ALSA: final selected sample format for capture: 24bit little-endian[/COLOR]
 [COLOR=#999999]ALSA: use 2 periods for capture[/COLOR]
 [COLOR=#999999]ALSA: final selected sample format for playback: 24bit little-endian[/COLOR]
 [COLOR=#999999]ALSA: use 2 periods for playback[/COLOR]
 [COLOR=#999999]ALSA: could not start playback (Broken pipe)[/COLOR]
 [COLOR=#999999]DRIVER NT: could not start driver[/COLOR]
 [COLOR=#999999]cannot start driver[/COLOR]
 [COLOR=#999999]10:31:29.028 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]10:31:29.028 Post-shutdown script...[/COLOR]
 [COLOR=#990099]10:31:29.028 killall jackd[/COLOR]
 [COLOR=#999999]jackd: no process found[/COLOR]
 [COLOR=#999999]10:31:29.434 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#ff0000]10:31:30.825 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]

The weird thing is it is trying to tell me to alter a line in a file that doesnt exist. I know the file exists in the /etc/security directory, so altered that one instead and put in the line [COLOR=#999999]@audio   -  memlock    1436520[COLOR=Black] (note that [/COLOR][/COLOR][COLOR=#999999]@audio   -  memlock    unlimited [COLOR=Black]was not actually originally in the limits.conf file). After I did this it keeps coming back with the same message. As a side note if someone could tell me what the # at the beginning of each line means I would be grateful

Anyway, aside from that the headphone output on the fast track works when listening to Music player so it is talking to the laptop (outside of the Jack environment). Havnt tried any of the inputs or outputs as yet.

thanks for the help 


[/COLOR][/COLOR]

---

### Post by dsterry on 2010-10-09
I'm trying to get the same thing working. I can record straight to audacity using ALSA but would like to get jackd working so I can use rakarrak working with my guitar. I've found I can at cleast run jackd if I use the terminal and sudo jackd. I can get other things running with sudo as well like rakarakk and qjackctl but I've not had any audio make it through jack. I'll post again if I get it working...hope you'll do the same.

---

### Post by dsterry on 2010-10-10
I followed the instructions at [http://ubuntuforums.org/archive/index.php/t-447744.html](http://ubuntuforums.org/archive/index.php/t-447744.html) and I'm in good shape. In short, open qjackctl (still using sudo for these) and go into setup. Then set frames/period to 256, interface and input device to the Fast Track with Realtime checked.

---

### Post by dogbin on 2010-11-01
I followed those instruction and still get the same message. its still trying to tell me to change the non-existent file to change memlock. It appears that the error occurs here

p, li { white-space: pre-wrap; } [COLOR=#999999]Memory locking is unlimited - this is dangerous. You should probably alter the line:[/COLOR]
 [COLOR=#999999]     @audio   -  memlock    unlimited[/COLOR]
 [COLOR=#999999]in your /etc/limits.conf to read:[/COLOR]
 [COLOR=#999999]     @audio   -  memlock    1436520[/COLOR]
 [COLOR=#999999]no message buffer overruns[/COLOR]
 [COLOR=#999999]JACK compiled with System V SHM support.[/COLOR]
 [COLOR=#999999]loading driver ..[/COLOR]
 [COLOR=#999999]SSE2 detected[/COLOR]
 [COLOR=#999999]apparent rate = 44100[/COLOR]
 [COLOR=#999999]creating alsa driver ... hw:1|hw:1|128|2|44100|2|2|nomon|swmeter|-|16bit[/COLOR]
 [COLOR=#999999]control device hw:1[/COLOR]
 [COLOR=#999999]configuring for 44100Hz, period = 128 frames (2.9 ms), buffer = 2 periods[/COLOR]
 [COLOR=#999999]ALSA: final selected sample format for capture: 16bit little-endian[/COLOR]
 [COLOR=#999999]ALSA: use 2 periods for capture[/COLOR]
 [COLOR=#999999]ALSA: final selected sample format for playback: 16bit little-endian[/COLOR]
 [COLOR=#999999]ALSA: use 2 periods for playback[/COLOR]
 [COLOR=#999999]ALSA: could not start playback (Broken pipe)[/COLOR]
 [COLOR=#999999]DRIVER NT: could not start driver[/COLOR]
 [COLOR=#999999]cannot start driver[/COLOR]
 [COLOR=#999999]19:26:22.219 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]19:26:22.220 Post-shutdown script...[/COLOR]
 [COLOR=#990099]19:26:22.220 killall jackd[/COLOR]
 [COLOR=#999999]jackd: no process found[/COLOR]
 [COLOR=#999999]19:26:22.631 Post-shutdown script terminated with exit status=256.[/COLOR]

[COLOR=#999999][/COLOR]
[COLOR=#999999][COLOR=Black]The error appears to occur with the line 
[/COLOR][/COLOR]

[COLOR=#999999][/COLOR]
[COLOR=#999999]ALSA: use 2 periods for playback[/COLOR]
 [COLOR=#999999]ALSA: could not start playback (Broken pipe)[/COLOR]

[COLOR=#999999][/COLOR]
[COLOR=#999999][COLOR=Black]So i changed frames/periods  too 3 and then 24. Still SAME MESSAGE. Very, very close to puting on a windows partition though i really dont want to cos i hate microsoft[/COLOR]
[/COLOR]

---

### Post by dogbin on 2010-11-01
Well i fixed the memlock situation by editing the /etc/security/limits.d/audio.conf file that jack creates I think.... i found the line 

[COLOR=#999999]@audio   -  memlock    unlimited

[COLOR=Black]and changed it to [/COLOR]

[/COLOR][COLOR=#999999]@audio   -  memlock    1436520[COLOR=Black]

Still get the same message about a broken pipe though

[/COLOR][/COLOR] p, li { white-space: pre-wrap; } ALSA: could not start playback (Broken pipe)
 DRIVER NT: could not start driver
 cannot start driver


Help would be appreciated

---

### Post by dogbin on 2011-01-05
I moved this problem to another post

[http://ubuntuforums.org/showthread.php?p=10310472#post10310472](http://ubuntuforums.org/showthread.php?p=10310472#post10310472)

seems I my usb in my laptop is buggy so I am going to have to get a USB express card to get it to work

Cheers

---

