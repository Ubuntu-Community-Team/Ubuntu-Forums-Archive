---
title: "couple issues nothing huge"
date: 2011-09-15
forum: Hardware
---

### Post by ables on 2011-09-15
when im in ubunto and i plug in my headphones it still plays thru the speakers, it doesnt even recognized that they are plugged in.

also my camera on tinychat works but my mic does not.

nothin else major so far.

im on a toshiba satellite l655-s5150 if that makes a difference

---

### Post by grahammechanical on 2011-09-15
Click on the sound icon and select Sound Preferences. Then select the Out put tab and make sure that the headphone socket is selected as the out put device and that the output is not muted or too low.

Do the same for Input to get the microphone working.

Or tell us that you have already tried this.

Regards.

---

### Post by Toz on 2011-09-15
> **ables said:**
> when im in ubunto and i plug in my headphones it still plays thru the speakers, it doesnt even recognized that they are plugged in.

also my camera on tinychat works but my mic does not.

nothin else major so far.

im on a toshiba satellite l655-s5150 if that makes a difference
Regarding the headphones/speaker problem, edit the file **/etc/modprobe.d/alsa-base.conf** as root (from the command line):
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```
and append to the end of the file, the following line:
```
options snd-hda-intel model=thinkpad
```
Save the file and reboot.

---

### Post by ables on 2011-09-15
what toz suggested worked for the headphones.

as far as the mic, it works but the sound is really low. i have alsa mixer but no options for my mic...any suggestions.

---

### Post by Toz on 2011-09-15
> **ables said:**
> as far as the mic, it works but the sound is really low. i have alsa mixer but no options for my mic...any suggestions.

Can you post the results of the following command?
```
amixer
```

---

### Post by ables on 2011-09-15
> Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 74
  Mono:
  Front Left: Playback 60 [81%] [-14.00dB] [on]
  Front Right: Playback 60 [81%] [-14.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 254 [100%] [0.20dB]
  Front Right: Playback 254 [100%] [0.20dB]
Simple mixer control 'Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 7
  Mono: Playback 2 [29%] [-20.00dB] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 80
  Front Left: Capture 78 [98%] [4.00dB] [on]
  Front Right: Capture 78 [98%] [4.00dB] [on]
Simple mixer control 'Analog Mic Boost',0
  Capabilities: cenum
  Items: '0dB' '10dB' '20dB' '30dB' '40dB'
  Item0: '0dB'


btw thx 4 the headphone tip, worked rite away. do u have any websites that give guides on how to learn linux more in depth?

---

### Post by Toz on 2011-09-15
> **ables said:**
> btw thx 4 the headphone tip, worked rite away. do u have any websites that give guides on how to learn linux more in depth?

Is that the whole of the contents of the results of that command? It looks like its missing some info. Try doing it this way:
```
amixer > axmixer.txt
```
then open the file amixer.txt and copy/paste the contents here.

Did you follow the instructions that @grahammechanical posted earlier? Have you double-checked that its not muted? If there's a Mic Boost entry, have you tried adjusting it?

As for websites, I'm certain there are many, but I learned hands-on. The official Ubuntu Documentation ([https://help.ubuntu.com/]("https://help.ubuntu.com/")) is a good place to start.

---

### Post by ables on 2011-09-15
where does the file go to when i save it as u instructed with the
> amixer > amixer.txt

i've searched and neither i nor the computer has found it. 

i apologize, yes i have done what graham said and it did not work.

when i am in "sound preferences" the only input or output option that i do have is "internal audio analog sterio" so it is clicked.

i ran the "amixer" command again in terminal and got this again.

> Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 74
  Mono:
  Front Left: Playback 60 [81%] [-14.00dB] [on]
  Front Right: Playback 60 [81%] [-14.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 254 [100%] [0.20dB]
  Front Right: Playback 254 [100%] [0.20dB]
Simple mixer control 'Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 7
  Mono: Playback 2 [29%] [-20.00dB] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 80
  Front Left: Capture 78 [98%] [4.00dB] [on]
  Front Right: Capture 78 [98%] [4.00dB] [on]
Simple mixer control 'Analog Mic Boost',0
  Capabilities: cenum
  Items: '0dB' '10dB' '20dB' '30dB' '40dB'
  Item0: '0dB'

---

### Post by Toz on 2011-09-15
> **ables said:**
> where does the file go to when i save it as u instructed with the


i've searched and neither i nor the computer has found it.
It would be in the current directory. Try this instead:
```
amixer > ~/amixer.txt
``` 
then look for the file in your home directory.

> i apologize, yes i have done what graham said and it did not work.
ok, thanks for confirming.

> when i am in "sound preferences" the only input or output option that i do have is "internal audio analog sterio" so it is clicked.
Do you have a "Select Controls" button on the bottom left? If so, click on it and make sure all of the microphone entries are selected then make sure all are not muted and/or with appropriate volume.

---

### Post by ables on 2011-09-15
no i do not have a "select controls" button unfortunately. 


here is the text from the amixer.txt file:

```
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 74
  Mono:
  Front Left: Playback 60 [81%] [-14.00dB] [on]
  Front Right: Playback 60 [81%] [-14.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 254 [100%] [0.20dB]
  Front Right: Playback 254 [100%] [0.20dB]
Simple mixer control 'Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 7
  Mono: Playback 2 [29%] [-20.00dB] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 80
  Front Left: Capture 78 [98%] [4.00dB] [on]
  Front Right: Capture 78 [98%] [4.00dB] [on]
Simple mixer control 'Analog Mic Boost',0
  Capabilities: cenum
  Items: '0dB' '10dB' '20dB' '30dB' '40dB'
  Item0: '0dB'
```

---

### Post by Toz on 2011-09-16
Does increasing the value of "Analog Mic Boost" in alsamixer make a difference?

---

### Post by ables on 2011-09-16
nope i tried and i had the mic adjustment to full on some chat clients aswell and nothing. o well, that laptop was junk i traded it for a dell and so far the dell is running smooth, it just doesnt seem to want to connect to the internet on a wired connection, but im sure i can search and find a solution for that.


thank for the help both of you guys by the way, you were each of great help.

---

### Post by Toz on 2011-09-16
> **ables said:**
> o well, that laptop was junk i traded it for a dell

Ahhhh, the old "wipe the slate clean" fix. Cool. Enjoy the new laptop.

---

