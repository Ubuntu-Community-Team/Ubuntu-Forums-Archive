---
title: "hdmi audio output with intel chipset"
date: 2009-04-15
forum: Hardware
---

### Post by limanoit on 2009-04-15
hi guys. 

any idea how to output audio over HDMI port with intel 945gm chipset ? 
hdmi video does output the video but no sound. i tested this hardware on windows and it works fine.  i havent tried it on fedora. but any suggestion how to make this work ? 

i am using ubuntu 9.04 beta .. with i guess x86 intel 2.6 graphic driver that comes with it by default and 

glxinfo | grep render tells me this 
direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) 945GME GEM 20090114 x86/MMX/SSE2


//and it looks like i have the  HDMI port detected
```
desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

//and here too
```
desktop:~$ asoundconf list
Names of available sound cards:
```

it tried "test" under system/preference/sound and it does  not output any sound. tried playing .ogg file and not working.. is there any command / any way how i can make this work ? thanks 

Intel

---

### Post by ahbart on 2009-04-15
My digital output is by default always off. maybe that's the case with your system. 
Open gnome volume manager - settings/preferences button - and select the suspected devices. When done, I get a new tab in the volume manager with switches. Including IEC958 in my case.
Could that be the case?

---

### Post by limanoit on 2009-04-15
@ahbart

i installed gnome-volume-manager but 
Open gnome volume manager - settings/preferences button - and select the suspected devices 

i dont find any gui to that manager ? 
it is kind of a  mounting command ? 

and i tried ```
speaker-test -Dplughw:0,3
//0, 3 is my hdmi devices. tutorial that i found on here //http://wiki.foxmediasystems.com/index.php/Ubuntu_Intel_HDMI_Audio

speaker-test 1.0.18

Playback device is plughw:0,3
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 16384
Period size range from 32 to 8192
Using max buffer size 16384
Periods = 4
was set period_size = 4096
was set buffer_size = 16384
 0 - Front Left
Time per period = 2.646683
 0 - Front Left
Time per period = 2.986585
 0 - Front Left
Time per period = 2.986551
 0 - Front Left
Time per period = 2.986590
 0 - Front Left
Time per period = 2.986559
 0 - Front Left
Time per period = 2.986546
 0 - Front Left
Time per period = 2.986597
 0 - Front Left
Time per period = 2.986540
 0 - Front Left
Time per period = 2.986656
 0 - Front Left
Time per period = 2.986530
 0 - Front Left
Time per period = 2.986458
 0 - Front Left
Time per period = 2.986647
 0 - Front Left
Time per period = 2.986462
 0 - Front Left
Time per period = 2.986551
 0 - Front Left
Time per period = 2.986564
 0 - Front Left
Time per period = 2.986563
 0 - Front Left
Time per period = 2.986578
 0 - Front Left
Time per period = 2.986613
 0 - Front Left

```

it looks like it is working but there is actually no sound output . i have made sure that     the sound is not muted. any ideas ? thanks

---

### Post by limanoit on 2009-04-15
oh got what you said it actually is gnome volume applet. i am trying ....

---

### Post by ahbart on 2009-04-15
Damn. Sorry about that.

---

### Post by limanoit on 2009-04-15
Open gnome volume manager - settings/preferences button - and select the suspected devices. When done, I get a new tab in the volume manager with switches. Including IEC958 in my case.

tried this and hdmi audio still not working ...

---

