---
title: "Conflict between webcam and tvtime"
date: 2010-06-02
forum: Hardware
---

### Post by Ghandy on 2010-06-02
Dear friends, 

I'm fighting with my  webcam and tvtime already a few hours, as researched several pages  without success. 
When I try to run tvtime,  and open and off and appears in the shell: 
tvtime-d / dev/video1 
Running tvtime 1.0.2. 
Reading configuration  from / home / ghandy / .tvtime / tvtime.xml 
Found "USB Device 0x93a:  0x260e: USB Audio (hw: 1,0)" 
Channels count non  availableghandy @ seneca: ~ $ 

This webcam and usb DLINK  DSB-C320 when I remove it tvtime works, what can I do. 

Thank you for listening

---

### Post by Chronos6 on 2010-07-11
I have a the same problem. 

chronos@chronos-desktop:~$ tvtime
Futtatás: tvtime 1.0.2.
Konfiguráció beolvasása: /etc/tvtime/tvtime.xml
Konfiguráció beolvasása: /home/chronos/.tvtime/tvtime.xml
Found "USB Device 0x46d:0x802 : USB Audio (hw:1,0)" Channels count non available



chronos@chronos-desktop:~$ tvtime --device=/dev/video1
Futtatás: tvtime 1.0.2.
Konfiguráció beolvasása: /etc/tvtime/tvtime.xml
Konfiguráció beolvasása: /home/chronos/.tvtime/tvtime.xml
Found "USB Device 0x46d:0x802 : USB Audio (hw:1,0)"
Channels count non available

---

### Post by tominto on 2011-01-27
Did you figure it out?  I am having the same problem

---

### Post by ene_dene on 2011-11-05
Same here in 11.10. tvtime works fine if camera is unplugged, but when plugged it gives that error although I explicitly guide the system to right video device.

---

### Post by Dilutu on 2011-12-03
I should add myself to this list of "same here".  I created fixed symlinks with udev and modified tvtime.xml accordingly, it works when I check with VLC but not tvtime.....
Th.

---

### Post by Dilutu on 2011-12-03
Well I just tried xdtv and no problems here....Th.

---

