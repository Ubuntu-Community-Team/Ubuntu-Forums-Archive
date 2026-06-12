---
title: "HDMI ALC663/nVidia GeForce 9600m"
date: 2009-03-08
forum: Hardware
---

### Post by tstivers1990 on 2009-03-08
I am trying to get audio through hdmi working, i'm a linux newb, but i know a bit, i have video working through hdmi fine, but audio i am clueless

here is aplay -l output

```
tony@tony-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC663 Analog [ALC663 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC663 Digital [ALC663 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

i would assume card 0, device 1 is my hdmi, but i am not sure

my laptop is an asus m70vm-X1
ubuntu version is 8.10
alsa 1.0.17
using nvidia 177 drivers
fresh install, fully updated

---

### Post by tstivers1990 on 2009-03-08
also, i have enabled and checked the "IEC958" and "IEC958 Default PCM" switches, to no avail

---

### Post by chrisbw66 on 2009-03-21
If you're feeling brave I think you probably need to look at this thread - [http://ubuntuforums.org/showthread.php?t=1052994](http://ubuntuforums.org/showthread.php?t=1052994)

I am considering upgrading Alsa to version 1.0.19 myself but as it can't be done in Synaptic yet it has to be done using a script to do the install work for you as detailed on the thread mentioned above & in the following post [http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

If its not too important you could wait for the packages to be added to the Ubuntu repositories - but one post suggests that this could be 6 months from the release of the original alsa release - maybe 4 months away.

If you absolutely must have sound with HDMI - like me ! - then I think this is your best option - just make sure that you back up any important data first, or better still your complete hard drive. Also it looks like you may need to rerun the script periodically - if a kernel upgrade is made in Synaptic for example, and also when the Alsa packages get upgraded. When the Alsa packages are upgraded to 1.0.19 you won't need to rerun the script again of course.... :) 

Hope that helps a bit.
Chris.

---

### Post by Ancanus on 2009-12-08
Bump! 

Same issue as poster.

ASUS G50V-A2
Ubuntu 9.10
Alsa 1.0.21
nVidia: 190.42

HDMI Video works, audio does not.

```
ancanus@ancanus-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC663 Analog [ALC663 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC663 Digital [ALC663 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
``````

ancanus@ancanus-laptop:~$ aplay -L
front:CARD=Intel,DEV=0
    HDA Intel, ALC663 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC663 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC663 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC663 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC663 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC663 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC663 Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)

```

---

### Post by tstivers1990 on 2009-12-09
I'm also still having this issue and would be willing to help within my abilities.

---

### Post by Ancanus on 2009-12-09
I'm about to give up with this. T_T

Things tried so far:


[LIST]
[*]Alsa-drivers: updated to 1.0.21
[*]Alsa-drivers: applied patch @ patch_nvhdmi.c & recompiled source
[*]Alsa-libs: updated to 1.0.21
[*]Alsa-utils: updated to 1.0.21
[*]nVidia-drivers: updated to 190.45
[*]Alsamixer: Unmuted SPDIF & SPDIF PCM
[*]alsa-base.conf: Tried every possible combination of models at 'options snd-hda-intel model=xxxx'
[/LIST]


Basically at least the top 40 google hits on this topic and still,
"speaker-test -D iec958 -c2" gives me no sound on the TV.

Perhaps the fix for this hasn't been found yet? I was unable to find any bug report filed as well.

---

### Post by tstivers1990 on 2009-12-09
from what i had gathered when i was working on this, was that it wasn't even being worked on. this is one of the reasons i don't use linux for much other than servers, it just hasn't proven it's capable of being a sufficient desktop os yet. once all these issues are worked out of it, then it will be the best operating system for servers and desktops. until then though, nobody is going to deal with problems like this if there is a solution, such as installing windows, therefore linux doesn't have the user base it needs, therefore it doesn't get these kinks worked out.

---

### Post by Ancanus on 2009-12-09
Oi! I got it!

Basically, you have to download the Linux Drivers at Realtek
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false)
Then you follow the manual installation instructions on the Readme.txt. [I skipped Steps 2 and 4] (Nothing complicated, configure, make, make install, and run some configuration scripts)


Doing this enabled a new HDMI profile in System -> Preferences, which allows the audio to play on the TV.


Now I've gotta figure how to fix my headphone plug not working, since it reverted back to it's original state. :)

Let me know if you get it going.

```

ancanus@ancanus-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC663 Analog [ALC663 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC663 Digital [ALC663 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by tstivers1990 on 2009-12-09
bravo! i'm currently running windows 7 as it suits my needs for now, and i'm unable to test this right now as my job takes too much time, and my job involves tech support, so the last thing i want to do when i get home, is mess with linux :P however on my next day off i may try it out to confirm whether it's a working solution or not, and depending on how much time i have and how motivated i am, i may work on a debian package for it and submit it.

---

### Post by tstivers1990 on 2009-12-09
also, as for the headphone plug, i'm not sure as i don't remember having that issue, and haven't played with linux in a while, but i'll check up on that too and see if there's a solution for it, i know headphones worked for me, but i don't remember if i had to do any hacks to get it working properly

---

### Post by tstivers1990 on 2009-12-16
OK, I got sick of Microsoft bugging me to activate every 5 minutes, so I decided to give Ubuntu another try. I installed 9.10, and HDMI, headphones, essentially everything but my G15 keyboard, and the dual mode touchpad, worked out of the box. So I'd say this issue has been resolved as of Ubuntu 9.10 karmic. Great job to the Ubuntu team :D

---

