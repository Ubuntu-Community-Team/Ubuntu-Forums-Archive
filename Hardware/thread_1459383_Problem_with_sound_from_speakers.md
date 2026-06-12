---
title: "Problem with sound from speakers"
date: 2010-04-21
forum: Hardware
---

### Post by ZooMpl on 2010-04-21
Hello,
Sorry for bad English - I'm from Poland .

Well.. Polish Ubuntu forum doesn't help me, so i search help in there. 

My problem : I have notebook MSI VR630 , with soundcard Realtek ALC888 , and laptop have speakers. 
In Ubuntu 9.04 if I plug headphones or external speakers , internal speakers has turn off. It's really good .
In Ubuntu 9.10 if I plug headphones or external speakers , internal speakers don't turn off ! It's no good. 

My Ubuntu have GNOME , i try alsamixer, gnome mixer, and i don't see "Speakers" to off. 

Sorry for bad English..

> Polish version :
Mój problem jest z laptopem MSI VR630 ,z kart&#261; d&#378;wi&#281;kow&#261; Realtek ALC888 i wbudowanymi g&#322;o&#347;nikami.
Na ubuntu 9.04 je&#347;li pod&#322;&#261;czy&#322;em s&#322;uchawki b&#261;d&#378; zewn&#281;trzne g&#322;o&#347;niki, nie by&#322;o problemu z wyciszeniem wbudowanych.
Na ubuntu 9.10 je&#347;li pod&#322;&#261;cze s&#322;uchawki b&#261;d&#378; zewn&#281;trzne g&#322;o&#347;niki, nie mog&#281; nigdzie wyciszy&#263; wbudowanych g&#322;o&#347;ników, nie ma takiej funkcji .

Any idea?
Please help.

---

### Post by lidex on 2010-04-22
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=targa-dig  
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels.
Go to "System>Preferences>Sound" and make sure the correct soundcard is default

---

