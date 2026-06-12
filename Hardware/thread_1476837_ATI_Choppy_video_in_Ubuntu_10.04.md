---
title: "ATI Choppy video in Ubuntu 10.04"
date: 2010-05-08
forum: Hardware
---

### Post by SOME1 on 2010-05-08
Hi, 

I am using ubuntu since 5.10 version, and thats my favorite os. 
I made a clean install of Ubuntu 10.04 on my ibm thinkpad t43p laptop with M24GL [Mobility FireGL V3200] video card. 
It works OK, execpt the graphic is little slow and I can't watch video's at all becouse it is choppy. 
I tried to watch it with totem and with xbmc - both work ok on previous ubuntu versions, but now the videos (sd & hd) are unwachable. 
I install vlc and the results there is better, but I still preffer fixing totem & xbmc if possible.
I saw that this version canceled the xorg.conf file so I don't know even where to begin fixing it. 

I search this forums and google but I can't find anything useful. 

thanks.

---

### Post by dino99 on 2010-05-08
is the "radeon" driver activated into hardware driver (system admin) ?

remove/purge others video drivers but xserver-xorg-video-radeon

---

### Post by SOME1 on 2010-05-08
thanks for reply. 
I am not sure I understand you. 
I am using raedon becouse ati drop the support for my card. 

thanks.

---

### Post by jataomm on 2010-05-08
I had a similar problem with a radeon card and getting the very latest updates, followed by a reboot appears to have fixed it.

---

### Post by SOME1 on 2010-05-08
thanks. 

I upgrade every day using "sudo apt-get dist-upgrade" command but it hasn't change anything. 
I checked again now and there is no new upgrades for me.

---

### Post by sheamuso on 2010-08-17
Sorry to open this old thread but did you manage to fix the problem? I've had the same issue since day one in Lucid and have used VLC to play videos but would like to get it fixed. I've an ATI card and AMD processor in a Packard Bell laptop.

Videos in a tiny window will work but full screen makes them unwatchable due to dropped frames.

Sheamus

---

### Post by lamaistres on 2010-08-17
Video playback is noticeably choppy in fullscreen mode using vx (does radeon fully support vx output?). Changing the video output to gl in vlc gave me much better results, but the cpu may work a little harder because I believe opengl is rendering the video through software.
Mplayer also gave better results, but the audio was out of sync with the video (easy fix though).
Totem has a limited vocabulary, so I don't know how to change its video output.

---

### Post by sheamuso on 2010-08-18
Thanks for the advice. I looked around and found this solution which fixed my problem, finally!

[http://www.niccolofavari.com/ubuntu-10.04-lucid-issues-with-external-monitor-and-ati-radeon-card](http://www.niccolofavari.com/ubuntu-10.04-lucid-issues-with-external-monitor-and-ati-radeon-card)

---

