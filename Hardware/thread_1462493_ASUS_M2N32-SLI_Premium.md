---
title: "ASUS M2N32-SLI Premium"
date: 2010-04-25
forum: Hardware
---

### Post by DoyleChris on 2010-04-25
I just installed Ubuntu on my computer for the first time on this motherboard ASUS M2N32-SLI Premium VISTA Edition and it seems to be working ok but the sound drivers are not working and everything else is if somebody could point me in the right direction for Soundmax Linux drivers.

---

### Post by chaz7201 on 2010-07-09
im new to ubuntu - but i also have that board in the ultra series. same audio though - 
i had to go to System -> Administration -> Users and Groups -> Advanced Settings -> User Privliages - click enable sound 

ALSO if thats not the quick fix try searching something about ALSA = its in the universe somewhere :D good luck

---

### Post by lidex on 2010-07-09
Have you checked your sound levels? Made sure sound not muted?
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

