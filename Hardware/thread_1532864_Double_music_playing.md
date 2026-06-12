---
title: "Double music playing"
date: 2010-07-17
forum: Hardware
---

### Post by jodlajodla on 2010-07-17
Hello!

I have problem with my computer, which playing music on audio output (my speakers) and motherboard speaker (intergrated). I need to switch off motherboard speaker, because I have speakers for music and I can switch on it when I need it. I tried to switch off motherboard speakers in BIOS, but there is no this option. In Ubuntu audio control panel is no any option to switch off it. 

Please help me :)

Thank you!

---

### Post by lidex on 2010-07-18
Use a mixer to mute/unmute/adjust levels.
**Alsamixer**
Using a Terminal="Applications->Accessories->Terminal"
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

---

### Post by jodlajodla on 2010-07-21
If I mute headphones there is no sound, but if I set headphones to minimal level there is little music on motherboard speaker. Other levels haven't got any effect. What can I do?

Thank you!

---

### Post by jodlajodla on 2010-09-10
Please help me, because I really need this information. Thank you!

---

### Post by lidex on 2010-09-14
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Enter your user password when prompted. Choose the upload option and provide a link for the output.

---

