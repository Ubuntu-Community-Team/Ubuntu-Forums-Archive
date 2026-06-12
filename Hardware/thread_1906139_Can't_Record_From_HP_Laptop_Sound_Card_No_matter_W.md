---
title: "Can't Record From HP Laptop Sound Card No matter What I Try."
date: 2012-01-08
forum: Hardware
---

### Post by The Little Book of Calm on 2012-01-08
p { margin-bottom: 0.21cm; }  I can't record any sound coming from my laptop's sound card what so ever.  Doesn't matter if I use sound recorder, audacity, desktop recorder or record it now. I have done it before using windows and Ubuntu but after upgrading to 11.10 and disliking it I down graded back to 10.10 which doesn’t want to record sound any more.
 

 I've tried various different threads to find a solution and can't find anything that helps.
 

 My laptop is a HP Compaq nx6325.
 

 It's running Ubuntu 10.10 maverick
 Kernel linux 2.6.35-22 generic.
 and 
 I think this is my sound card.  
 

 **** List of PLAYBACK Hardware Devices **** 
 card 0: SB [HDA ATI SB], device 0: AD198x Analog [AD198x Analog] 
   Subdevices: 1/1 
   Subdevice #0: subdevice #0 
 

 I've also tried youtubing for a solution but there doesn't seem to be anything working there.
 

 I'm not sure what to do or what other information you may need but any information would be greatly appreciated. Knowing me I've overlooked something stupidly simple.

---

### Post by madvinegar on 2012-01-13
Try to shut off one of your two speakers (i.e. by putting the sound balance all the way to the left) and see if the microphone will work.

If it does, download and install Pulse Audio Volume control from ubuntu software center, and on the 4th tab (input devices) shut off completely one of the two channels (i.e. the left one).

---

