---
title: "Sound cuts out until restart"
date: 2009-02-16
forum: Hardware
---

### Post by RealG187 on 2009-02-16
My sound on my laptop randomly stops working. Rhythmbox will freeze repetitivly. When I goto System --> Preferences --> Sound and try to do a test I get this message

> audiotestsrc wave=sine freq=512 !
audioconvert ! audioresample ! gconfaudiosink:
Failed to connect: Connection refused

When I restart it works but it happens again after a while. I don't want to restart every half hour when my sound stops working...

I just finished resarting and while my music was playing it started to "skip" like repeat this really bad sound and it gives the same message. This is really ****ing annoying :mad

---

### Post by neu2buntu on 2009-02-16
i think it is possible that pulseaudio is the culprit here, the next time your sound fails try ```
killall pulseaudio 
``` and ```
pulseaudio -D
``` in the terminal instead of rebooting... i suspect you need to change your system wide sound settings , here a veryusefull post to get most things right  
  [http://ubuntuforums.org/showthread.php?t=843012&highlight=markbuntu+pulseaudio+alsa+jack](http://ubuntuforums.org/showthread.php?t=843012&highlight=markbuntu+pulseaudio+alsa+jack)

---

### Post by RealG187 on 2009-02-23
> mpg@MIKED6:~$ killall pulseaudio
mpg@MIKED6:~$ pulseaudio -D]
pulseaudio: invalid option -- ']'
E: main.c: Failed to parse command line.
mpg@MIKED6:~$ pulseaudio -D
W: ltdl-bind-now.c: Failed to find original dlopen loader.
E: main.c: daemon startup failed.
mpg@MIKED6:~$ pulseaudio -D
W: ltdl-bind-now.c: Failed to find original dlopen loader.
E: main.c: daemon startup failed.
mpg@MIKED6:~$ pulseaudio -D
W: ltdl-bind-now.c: Failed to find original dlopen loader.
E: main.c: daemon startup failed.
mpg@MIKED6:~$ 

Fuuuuuuuuuuuuuuuu*************k

---

### Post by ReelExterminator on 2009-02-25
If the sound server has hung up, it might not respond to a simple kill. Try ```
sudo killall -9 pulseaudio
``` Type it twice to make sure it's really dead - if it is, it will give you an error the second time you run it telling you it's not running anymore. ```
pulseaudio -D
``` should work then.

---

### Post by RealG187 on 2009-02-26
Do I type that before or after it happens, funny is typing gksu killall pulseaudio solves this problem:

[http://ubuntuforums.org/showthread.php?p=6685605](http://ubuntuforums.org/showthread.php?p=6685605)

---

