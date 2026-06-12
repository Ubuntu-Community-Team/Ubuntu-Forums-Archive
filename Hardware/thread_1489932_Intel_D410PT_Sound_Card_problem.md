---
title: "Intel D410PT Sound Card problem"
date: 2010-05-21
forum: Hardware
---

### Post by komitaltrade on 2010-05-21
System is Ubuntu Lucid, kernel is 2.6.32-22-generic (but symptomsa are same with Karmic, 2.6.31-14-generic).

Advanced Linux Sound Architecture Driver Version 1.0.21.

HDA Intel at 0xe0380000 irq 22

**_Problem_**

Installation was perfect, system behavior is perfect, sound card dont display any deffect symptoms, but I dont have the sound (in windows I have, so, card is ok and headphones are plugged ok).

What can be problem and what is the solution?

---

### Post by lidex on 2010-05-23
Check levels in your mixers.
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
Use 'Edit -> Sound Card Properties' menu to enable elements.
Soundcard tab to select / adjust levels.

---

### Post by lidex on 2010-05-23
If you need more help I'll require more info. Post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

