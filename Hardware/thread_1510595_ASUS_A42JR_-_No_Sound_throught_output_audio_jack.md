---
title: "ASUS A42JR - No Sound throught output audio jack"
date: 2010-06-15
forum: Hardware
---

### Post by coliv_aja on 2010-06-15
Sorry, its maybe FAQ..
i bought ASUS A42JR and install Ubuntu Lucid Lynx...
Sound clear using internal speaker, but when i put speaker/headset to audio jack, no sound.
please help me, i have read some thread similar with my problem but can't solved my problem..
i'm very newbie on linux, please help me.

---

### Post by lidex on 2010-06-17
Need some info. Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by coliv_aja on 2010-06-18
thanks for respond, i'm very new in linux os . . . i'm very interesting with linux
i have ASUS A4JR intel i5
```

cholif@cholif-laptop:~$ uname -a
Linux cholif-laptop 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux
cholif@cholif-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
cholif@cholif-laptop:~$ 
cholif@cholif-laptop:~$ dpkg -l | grep "alsa"
ii  alsa-base                              1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                             1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                             4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                     0.10.28-1                                       GStreamer plugin for ALSA
cholif@cholif-laptop:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC269

==> /proc/asound/card1/codec#0 <==
Codec: ATI R6xx HDMI
cholif@cholif-laptop:~$ 


```

---

### Post by coliv_aja on 2010-06-18
and one more, i have been install  kubuntu-desktop from ubuntu software manager.
and i get kde desktop sure. but when i reboot .there's any duplicate booting menu, like this

1. ubuntu
2. ubuntu safe mode
3. ubuntu 
4. ubuntu safe mode
5. xxxx

any way to remove it, not look good i think , 
and yah, how to change splashscreen to ubuntu default, my splashscreen replaced with kubuntu ...
but not important. i'm very happy if can remove it

---

### Post by lidex on 2010-06-18
Try this.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
Logout/in.
Then
```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get install --reinstall alsa-utils alsa-oss alsa-base libasound2 libasound2-plugins linux-sound-base gstreamer0.10-alsa
```
**Reboot.**

---

### Post by coliv_aja on 2010-06-19
dude no such file 
```

 cholif@cholif-laptop:~$ rm -r ~/.pulse ~/.asound*  
rm: cannot remove `/home/cholif/.pulse': No such file or directory
rm: cannot remove `/home/cholif/.asound*': No such file or directory 
cholif@cholif-laptop:~$ sudo rm /etc/asound.conf rm: cannot remove `/etc/asound.conf': No such file or directory cholif@cholif-laptop:~$

```

can i skip this,

---

### Post by coliv_aja on 2010-06-19
dude, after i do all you command,
i still can't hear sound from my headset or speaker, just internal speaker can loud.
:confused:
=====================================================
i have been run 3 times command and 5 times reboot
i still can't hear anything from my headset.:confused:
WHY ITS HAPPEN TO ME  :guitar:

---

### Post by mcgentonk on 2010-06-20
same problem with my ASUS A42JR
i've tried script above, but doesn't get effect anymore....
give other solution please.....

---

