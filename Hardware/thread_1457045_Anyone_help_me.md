---
title: "Anyone help me ?"
date: 2010-04-18
forum: Hardware
---

### Post by mohammed-salman on 2010-04-18
**[FONT=Arial][SIZE=3]Hi everybody just I have small issue in my[COLOR=red] laptop DELL Inspiron 1564 (intel i3)[/COLOR] any one have driver or any file definition [COLOR=darkred]the sound card[/COLOR] to installation with ubuntu 9.04 - 64bit becauce only this problem with my ubuntu :confused:[/SIZE][/FONT]**

---

### Post by ajgreeny on 2010-04-18
It may not be a driver problem at all.  Run ```
alsamixer
``` in terminal to check that levels are not set too low, or something is muted.  Use cursor keys to move sideways and raise/lower levels, and "M" to mute/unmute channels, and Esc to save and quit.

---

### Post by mohammed-salman on 2010-04-18
thanx ajgreeny
I will try the experiment on the ubuntu system :popcorn:

---

### Post by mohammed-salman on 2010-04-19
its show in konsole this massage if i write  alsamixer

function snd_ctl_open failed for default: No such file or directory 


------------------
and if I press in sound button it's show this massage :
No Volume Control GStreemer Plugins and/or devices found .


plz help me :confused:

---

### Post by wilee-nilee on 2010-04-19
Have you right clicked on the volume icon>preferences to see if anything is turned down or muted.

---

### Post by ritendragoel on 2010-04-20
upgrade it to ubuntu 10.04. I am also using it intel core i3 64 bit.I think prob will be resolve.

---

### Post by P4man on 2010-04-20
I believe some of the newest core i3's have sound onchip, integrated in the cpu, along with the video chip. Thats really new though, so the first thing you probably want to do is update your ubuntu. Do you have all updates installed?

---

### Post by hsoulen on 2010-04-20
Have you tried loading the alsa backports package?

Seems to always help with sound issues on newer sound hardware.

1) Open Synaptic Package Mananger from System->Administration
2) Search for a package with a name like  "linux-backports-modules-alsa-karmic-generic" (it will have the name of  your distribution, karmic if you have 9.10, lucid if you are running the  10.04 LTS Beta etc.) and mark it for install
3) Reboot

Hank

---

