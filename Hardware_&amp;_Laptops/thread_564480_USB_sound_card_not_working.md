---
title: "USB sound card not working"
date: 2007-10-01
forum: Hardware &amp; Laptops
---

### Post by cesera on 2007-10-01
I have a little cheap USB sound card, works fine under W2K, doesn't even need drivers. When I plug it in it appears for about a minute in KInfoCentre and then it disappears again.
 
I am not sure what is going on, but it would be great if I could get it to work.
 
I am not sure what make it is, but the back says: Model PU552, USB 3D Sound, Made in China
 
This is what appears in KInfoCentre for about a minute:
 
[IMG]http://farm2.static.flickr.com/1103/1467930768_1b82814f51_d.jpg[/IMG]

---

### Post by victorgreen on 2007-10-05
I have something called GWC 5.1 channel Audio Adapter. The buttons on it control volume but I cant get it to give any sound output, gnome wont recognize it, nothing will.

---

### Post by victorgreen on 2007-10-05
I just had a VERY weird experience with sound. 

I went to the alsa website, downloaded and compiled the lasted release candidate of alsa (1.0.15rc3). My usb soundcard was recognized!! Sound came out, it was amazing. I unplugged it to make sure the onboard still worked, and it did. I was happy. Then I noticed that although my volume up down buttons still displayed the little volume bar rising/falling on the screen, but the volume didnt actually change. Only the gnome applet actually controlled sound. 

I then replugged the usb sound card and set prefs-sound to use it. No sound, no joy. All the sound came out of the onboard speakers. 

I restarted. Now prefs- sound doesnt show the usb sound card as an option and 
:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf8220000 irq 19

shows only my onboard when before it showed the USB as well. 

The volume controls work now too. 

Im really confused.

---

### Post by victorgreen on 2007-12-07
With gutsy and a fresh compile of latest alsa 1.0.15 everything works fine.

---

