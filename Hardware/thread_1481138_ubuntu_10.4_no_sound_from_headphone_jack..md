---
title: "ubuntu 10.4 no sound from headphone jack."
date: 2010-05-12
forum: Hardware
---

### Post by amirulrudy12 on 2010-05-12
hi i have a acer aspire timeline 4820T with a Realtek ALC259
.i have tried most of the method i found on the forum but there is still no sound from the headphone jack(laptop speaker have sound). im new to ubuntu so i hope anyone can guide me slowly.
this is my info:[http://www.alsa-project.org/db/?f=b1e96e1464a37a40642821eb7dabd6a6c5cbc7ac](http://www.alsa-project.org/db/?f=b1e96e1464a37a40642821eb7dabd6a6c5cbc7ac)
btw i have tried all of this:
ALC269
======
  basic            Basic preset
  quanta         Quanta FL1
  eeepc-p703    ASUS Eeepc P703 P900A
  eeepc-p901    ASUS Eeepc P901 S101
  fujitsu            FSC Amilo
  lifebook         Fujitsu Lifebook S6420
  auto        auto-config reading BIOS (default)
source:[http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt](http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt)

---

### Post by dino99 on 2010-05-12
install paprefs and gnome-alsamixer (tweak it as you need)

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by amirulrudy12 on 2010-05-12
thanks for the reply i will try when i get home :D.

---

### Post by lidex on 2010-05-13
Update your alsa install using the alsa-upgrade link in my sig.
Once that's finished: Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=acer  
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default.

---

### Post by amirulrudy12 on 2010-05-13
thank you so much for helping [lidex]("http://swiss.ubuntuforums.org/member.php?u=577099") n [dino99]("http://swiss.ubuntuforums.org/member.php?u=129712").the solution is i just reinstall ubuntu 10.4 n use the alsa update script that all.i hope it will help anyone with this problem :D.

[URL="http://img189.imageshack.us/i/screenshot1mt.png/"]
[/URL]

---

### Post by hismajesty on 2010-06-28
Hi,

I had the same problem on my Acer Aspire Timeline 4820TG with a ALC259 - headphone jack disabled the internal speakers but was not working. I followed many different attempts from forums but with no success.

Now I can confirm, that a fresh reinstall of Lucid Lynx 10.4 and directly afterwards an upgrade to ALSA 1.0.23 resolved the problem. I have no idea what was messed up before.

Good luck to everybody with the same problem! - Now I can go on to try to get my wireless card enabled on startup automatically... :/

---

### Post by coibyxqx on 2010-07-08
In my case, this solution works. [http://ubuntuforums.org/showthread.php?p=9562668#post9562668](http://ubuntuforums.org/showthread.php?p=9562668#post9562668)
Thanks to lidex anyway :)

---

### Post by titusDT on 2010-12-30
On Asus EeePC 10005Px the model=acer trick works fien thanks !

---

