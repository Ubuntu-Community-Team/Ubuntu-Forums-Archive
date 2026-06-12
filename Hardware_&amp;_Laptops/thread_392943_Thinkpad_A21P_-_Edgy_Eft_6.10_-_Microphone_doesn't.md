---
title: "Thinkpad A21P - Edgy Eft 6.10 - Microphone doesn't record sound"
date: 2007-03-25
forum: Hardware &amp; Laptops
---

### Post by miguipda on 2007-03-25
Hi,

on my IBM Thinkpad A21P, the sound works now on the 6.10 (he doesn't work under the 6.04).

If I type with a finger or if I blow in the microphone, I can hear sound on the integrated pc speaker BUT if I try to talk in skype or record in audacity no sound are received to those two programs. In audaicty the microphone is selected and his volume is in the maximum but nothing is recorded.

Here are attached the settings image of my kmix and alsamixer.

I sincerely appreciate your help to be able to use skype.

Have a nice day,

Miguipda ;-)

---

### Post by jlbiasini on 2007-03-27
Hello,

If you have correctly configure your sound drivers in alsa

if your mixer is also ok (capture on, input device micro, no mute etc...)

this is probably because your sound card don't accept to do several thing in the same time. To fix it you need a sound serveur. I'm using Esound but I'm under Debian and I don't know about Ubuntu. Anyway these two OS are close and I think that should be possible.

So install Esound (or an other sound serveur)
launch it (the command for Esound is esd)

then if it dont work either, you need to put your sound input on cd and then back to micro to enable the input.

You can launch it from the startup software menu with the option:
"esd -nobeeps" so you'll get not anoying noise when it launch.
you can use amixer (alsa package compoment) to automate the mixer configuration in the same startup software menu. 
 to do so type the command line :

> [color=red]$ amixer contents[/color]

for exemple it give me this:

> [color=green]numid=13,iface=MIXER,name='PCM Playback Volume'
  ; type=INTEGER,access=rw---,values=2,min=0,max=255,step=0
  : values=230,225
numid=5,iface=MIXER,name='CD Playback Switch'
  ; type=BOOLEAN,access=rw---,values=2
  : values=on,on
numid=4,iface=MIXER,name='CD Playback Volume'
  ; type=INTEGER,access=rw---,values=2,min=0,max=23,step=0
  : values=19,19
numid=3,iface=MIXER,name='Mic Playback Switch'
  ; type=BOOLEAN,access=rw---,values=2
  : values=off,off
numid=2,iface=MIXER,name='Mic Playback Volume'
  ; type=INTEGER,access=rw---,values=2,min=0,max=23,step=0
  : values=0,0
numid=7,iface=MIXER,name='Capture Switch'
  ; type=BOOLEAN,access=rw---,values=2
  : values=on,on
numid=6,iface=MIXER,name='Capture Volume'
  ; type=INTEGER,access=rw---,values=2,min=0,max=13,step=0
  : values=13,13
numid=9,iface=MIXER,name='IEC958 Playback Con Mask'
  ; type=IEC958,access=r----,values=1
  : values=?
numid=10,iface=MIXER,name='IEC958 Playback Pro Mask'
  ; type=IEC958,access=r----,values=1
  : values=?
numid=11,iface=MIXER,name='IEC958 Playback Default'
  ; type=IEC958,access=rw---,values=1
  : values=?
numid=12,iface=MIXER,name='IEC958 Playback Switch'
  ; type=BOOLEAN,access=rw---,values=1
  : values=off
numid=1,iface=MIXER,name='Front Playback Switch'
  ; type=BOOLEAN,access=rw---,values=2
  : values=on,on
[color=blue]numid=8,iface=MIXER,name='Input Source'[/color]
  ; type=ENUMERATED,access=rw---,values=1,items=2
  ; Item #0 'Mic'
  ; Item #1 'CD'
  : values=0[/color]

so search for a input source or sound input or something like that and look to the micro parameter for it (here item #0 'Mic' show the parameter should be 0)
In this exemple the parameter is already correctly set but it doesn't means that it works !!!
so let type now the command, the name of the controller and the parameter:
 
[color=red]amixer cset[/color] [color=blue]numid=8,iface=MIXER,name='Input Source'[/color] [color=yellow]0[/color]

put this command line in your startup software launch menu and if the problem is the same as for me it should be solve

bye

---

