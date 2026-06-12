---
title: "Audio through HDMI causes Freezing"
date: 2011-12-08
forum: Hardware
---

### Post by johnnybravos on 2011-12-08
First some background. I have been using my computer as an HTPC without incident on Ubuntu 10.10 for a couple of years now. I have the computer hooked up via HDMI to an Onkyo receiver. The receiver is hooked up to the TV via HDMI. Last week I tried to upgrade to ubuntu 11.10 and that went poorly. The upgrade worked but whenever I changed the volume on the receiver the computer would freeze.  

After some searching on this and other forums I removed Pulse Audio because I came across postings mentioning that Pulse audio did some auto detection via HDMI. After doing this with the help of the guides,  the freezing would only occur if I changed the volume when watching TV on the TV's antenna source. I gave up trying to fix this as my knowledge of Ubuntu is limited to following the guides posted on this and other forums. I reinstalled Ubuntu 10.10 and updated the necessary packages via update manager. Now freezing occurs when I have the receiver off and watching tv on the tvs antenna source. If I change the volume then the computer freezes. 

All this was not an issue before the attempted upgrade. The computer ran flawlessly no matter what I was doing with the TV or receiver. Is there any way to "dumb" down the computer's HDMI output so it just passes audio to the receiver without trying to detect the state of the receiver? I suspect that with the new reinstall and update I must have included some code that is trying to detect the state of the HDMI port on the receiver.  Incidentally I have just disabled the HDMI port through the BIOS and guess what no freezing but no sound either.   Should I remove Pulse Audio? I can't remember if I had Pulse working before I attempted the upgrade or not? 

Thanks for bearing with the long explanation but I want to eliminate that is is not a hardware issue because no hardware has changed.

---

### Post by johnnybravos on 2011-12-21
Well removing PulseAudio did the trick. Now my computer no longer freezes under any of the above scenarios. I guess I must have removed PulseAudio the first time around. For those of you who might be having a similar problem, I used Jeff Knocle's instructions on the following link  [http://www.jeffsplace.net/node/12](http://www.jeffsplace.net/node/12)

---

