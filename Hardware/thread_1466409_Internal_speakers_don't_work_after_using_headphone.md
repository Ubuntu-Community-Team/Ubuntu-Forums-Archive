---
title: "Internal speakers don't work after using headphones"
date: 2010-04-30
forum: Hardware
---

### Post by eshwar_andhavarapu on 2010-04-30
Hi,
I have a dell vostro 1720 with Lucid Lynx on it. Audio chip is intel hda. After connecting headphones/external speakers to the headphone jack, sound is channeled correctly to the external device only. but after removing the jack, sound does not return to the internal speakers. usually a restart fixes it or using alsamixer in terminal i have to increase volume of speakers manually. any fixes?

---

### Post by bas2 on 2010-04-30
try plugging the headphones in and out again that could help sometimes

---

### Post by eshwar_andhavarapu on 2010-04-30
> **bas2 said:**
> try plugging the headphones in and out again that could help sometimes

i've tried that. no luck :(

---

### Post by Veikk0 on 2010-04-30
It could be a problem with the laptop's motherboard itself. In most laptops plugging in the headphone/audio jack activates a mechanism that tells the computer to cut off sound from internal speakers. Sometimes this mechanism is easily broken... it happened to our family laptop:(

If it's software related I've no idea what it is. Maybe old threads could help?

---

### Post by eshwar_andhavarapu on 2010-05-01
> **Veikk0 said:**
> It could be a problem with the laptop's motherboard itself. In most laptops plugging in the headphone/audio jack activates a mechanism that tells the computer to cut off sound from internal speakers. Sometimes this mechanism is easily broken... it happened to our family laptop:(

If it's software related I've no idea what it is. Maybe old threads could help?

its quite weird because its behaviour is not consistent with a fault. i mean it definitely does not work after headphones but works after restart.

---

### Post by lidex on 2010-05-02
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by eshwar_andhavarapu on 2010-05-03
> **lidex said:**
> Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

Here is what i get:

```
eshwar@alexander:~$ uname -a
Linux alexander 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64 GNU/Linux
eshwar@alexander:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
eshwar@alexander:~$ cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.21.
eshwar@alexander:~$ head -n 1 /proc/asound/card
card0/ cards  
eshwar@alexander:~$ head -n 1 /proc/asound/card0/codec#0 
Codec: IDT 92HD81B1C5
eshwar@alexander:~$ 

```

The laptop is a Dell Vostro 1720 with Intel HDA.

---

### Post by lidex on 2010-05-04
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=dell-s14 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels.
Go to "System>Preferences>Sound" and make sure the correct soundcard is default.

---

### Post by eshwar_andhavarapu on 2010-05-05
> **lidex said:**
> Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=dell-s14 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels.
Go to "System>Preferences>Sound" and make sure the correct soundcard is default.

thanks lidex! that seems to have solved the problem but i noticed a small change. Before the change, the columns in alsamixer where master volume, headphone, speaker and then PCM. now after the change, speaker has changed to headphone 1. 

could you perhaps be kind enough to explain what the change did? my guess is it forces a different hardware model to be used as a basis for alsa.

---

### Post by dino99 on 2010-05-05
install , if not , paprefs and gnome-alsamixer (tweak it as you need)

---

### Post by vtdr on 2010-05-05
I have the same problem and my output is:

```
uname -a
Linux cris-laptop 2.6.31-21-generic #59-Ubuntu SMP Wed Mar 24 07:28:56 UTC 2010 i686 GNU/Linux

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Modem [ATI IXP Modem], device 0: ATI IXP MC97 [ATI IXP MC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.20.

head -n 1 /proc/asound/card0/codec97#0/ac97#0-0
0-0/0: Realtek ALC250 rev 2
```

Toshiba P30-128 laptop

Any suggestion?

Many thanks to all
vtdr

---

### Post by dino99 on 2010-05-05
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by dino99 on 2010-05-05
> **vtdr said:**
> I have the same problem and my output is:

```
uname -a
Linux cris-laptop 2.6.31-21-generic #59-Ubuntu SMP Wed Mar 24 07:28:56 UTC 2010 i686 GNU/Linux

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Modem [ATI IXP Modem], device 0: ATI IXP MC97 [ATI IXP MC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.20.

head -n 1 /proc/asound/card0/codec97#0/ac97#0-0
0-0/0: Realtek ALC250 rev 2
```

Toshiba P30-128 laptop

Any suggestion?

Many thanks to all
vtdr

may install toshset and toshutils with synaptic

---

### Post by vtdr on 2010-05-05
Hi dino99,
thank you for your reply, I'll try your advices...

vtdr

---

### Post by vtdr on 2010-05-05
Hi dino99,

I tried your advices> may install toshset and toshutils with synaptic

and this is what I get:```
-laptop:~$ toshset
required kernel toshiba support not enabled.
```

I can tell you that my laptop has always worked flawlessly, problem started when I plugged-in headphones and the only consequence is the speakers muting... 

vtdr

---

### Post by lidex on 2010-05-05
> **eshwar_andhavarapu said:**
> thanks lidex! that seems to have solved the problem but i noticed a small change. Before the change, the columns in alsamixer where master volume, headphone, speaker and then PCM. now after the change, speaker has changed to headphone 1. 

could you perhaps be kind enough to explain what the change did? my guess is it forces a different hardware model to be used as a basis for alsa.
You're welcome. Please mark the thread as solved using 'Thread Tools' up top.
Right, the default configuration was not routing audio properly for the pin setup on your motherboard. This just tells alsa the correct model.

---

