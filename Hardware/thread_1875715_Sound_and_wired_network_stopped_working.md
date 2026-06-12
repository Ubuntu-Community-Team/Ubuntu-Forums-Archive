---
title: "Sound and wired network stopped working"
date: 2011-11-05
forum: Hardware
---

### Post by alienlog on 2011-11-05
Hello Everyone,

I have upgraded to Oneiric from Natty a week ago and currently I'm not enjoying it at all :(
Upgrade process broke down everything and I had to use the alternate CD to install Oneiric. After 2 days of battle, the computer was nearly usable as it was before the upgrade. :P

Unfortunately, about 3 days ago, the sound stopped working and after reboot, the wired network stopped working too. I can still use WIFI so I can update the notebook easily.

During these 3 days I've tried a lot of things and nothing worked to get back the lost functionality.

Here comes the technical details :

[LIST]
[*]Phonon shows only dummy output (I got a dialog box saying KDE can't find the sound card anymore)
[*]I tried to remove .kde and .pulse directory but it didn't change anything
[*]Alsa seems to detect it : [http://www.alsa-project.org/db/?f=e40f5d5080b04d8e1b1635c1544dea9d9c204e78](http://www.alsa-project.org/db/?f=e40f5d5080b04d8e1b1635c1544dea9d9c204e78)
[*]aplay too
[/LIST]
```
aplay -l
**** Liste des Périphériques Matériels PLAYBACK ****
carte 0: Intel [HDA Intel], périphérique 0: STAC92xx Analog [STAC92xx Analog]
  Sous-périphériques: 0/1
  Sous-périphérique #0: subdevice #0
carte 0: Intel [HDA Intel], périphérique 1: STAC92xx Digital [STAC92xx Digital]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0
carte 0: Intel [HDA Intel], périphérique 3: HDMI 0 [HDMI 0]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0
```
[LIST]
[*]i tried this : [http://ubuntuforums.org/showthread.php?t=1316634&page=6](http://ubuntuforums.org/showthread.php?t=1316634&page=6)
[*]About the wired network it says "not connected" when I plug the cable
[*]It connected briefly yesterday after a reboot but stopped working again after the next reboot
[/LIST]

I know a few things about computers, but this time I don't think I 'm able to solve it on my own. I feel that both problem are related somehow.

Thanks for your help

---

### Post by alienlog on 2011-11-05
Ok I think I've solved my wired network problem.
The issue lied in the Network-manager. The ethernet was restricted to a disconnected interface. I put it to "any" and it connected immediately.

I don't know how this could happen since I'm on a laptop and nothing was removed.

Maybe something similar happened to the sound card ? How Phonon can detect the hardware again ?

I tried to compile alsa but it fails no matter what I try(with or without module-assistant)

---

### Post by alienlog on 2011-11-08
I think it's time for an update :
Following the Ac procedure :
```
Sound cards recognized by the system:
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
Sound cards recognized by ALSA:
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
Sound cards recognized by ALSA, and activated:
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)

```Then aplay -l
> **** Liste des Périphériques Matériels PLAYBACK ****
carte 0: Intel [HDA Intel], périphérique 0: STAC92xx Analog [STAC92xx Analog]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0
carte 0: Intel [HDA Intel], périphérique 1: STAC92xx Digital [STAC92xx Digital]
  Sous-périphériques: 0/1
  Sous-périphérique #0: subdevice #0
carte 0: Intel [HDA Intel], périphérique 3: HDMI 0 [HDMI 0]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0But when i launch Phonon i get this message you can see in attachment phonon.png (It's in french but it says my soundcard is not detected anymore and if I wish to remove it permanently)
In attachment phonon1.png i only have dummy output.
But in alsamixer.png everything seems fine !

As a reminder it's notebook, I can't remove the soundcard !
I really don't understand what's happening. Please help !

---

### Post by lkjoel on 2011-11-10
Could you post the screenshot when you click on: "Configuration des périphéries audio"?

---

### Post by alienlog on 2011-11-11
Thanks a lot for helping me out

There is no hardware detected. Screenshot called phonon3.png

---

### Post by lkjoel on 2011-11-11
Try following procedure Ae of this: [https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit](https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit)

---

### Post by alienlog on 2011-11-11
I was using version current-updates. I switch back to version current as stated in the procedure.

Unfortunatly the "aplay -l" command as the same output as before. No NVidia HDMI. I'm guessing it's because the laptop is quite old. The graphic card is a Geforce 9600M GT.
Should I continue the procedure with another device ?

Also this command "[COLOR=Black][FONT=Courier New]grep "eld_valid *1" /proc/asound/NVidia/eld*[/FONT][/COLOR][COLOR=#000000][FONT=Arial]" returns no match found. Actually, there is no NVidia directory. I only find "Intel".
[/FONT][/COLOR]

---

### Post by lkjoel on 2011-11-11
Yeah, try using another device.
Use current, not current-updates

---

### Post by alienlog on 2011-11-12
I made some experiments. Still no sound but I got some devices showing. I'm not sure if it's a good thing or a bad thing.

So here what I did :
I skipped the part about "eld" since I don't have any.
I entered this comma[COLOR=Black]nd : [COLOR=Black][FONT=Courier New]sudo update-initramfs -u[/FONT][/COLOR]
I [/COLOR][COLOR=black]edited this file [/COLOR][COLOR=black][FONT=Courier New]/etc/pulse/default.pa to add this line : load-module module-alsa-sink device=hw:0,0
in the static loading part.
Then I removed all cache :
[/FONT][/COLOR][COLOR=Black][COLOR=Black][FONT=Courier New]rm -rf ~/.pulse ~/.asound* ~/.pulse-cookie[/FONT][/COLOR]
[/COLOR] [COLOR=#000000][FONT=Courier New][COLOR=black]and finally a reboot.
[/COLOR]
After login, KDE gave me the message in attachments. I also added some screenshots from Phonon. That's a lot of devices but none is working. I tested each one of them.

Any idea ? I think it stopped working after kernel update [/FONT][/COLOR][COLOR=#000000][FONT=Courier New]3.0.0-13[/FONT][/COLOR]. But thats was not the only update so I can't be sure.


[COLOR=Black] [COLOR=#ffffff][FONT=Courier New]


[/FONT][/COLOR][/COLOR]

---

### Post by alienlog on 2011-11-12
Just to keep updates, I tried to boot an earlier version of kernel but it didn't brought back the sound. I tried 3.0.0-12 and 2.6.38.

---

