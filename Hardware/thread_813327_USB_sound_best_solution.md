---
title: "USB sound best solution"
date: 2008-05-30
forum: Hardware
---

### Post by tweston on 2008-05-30
IMO: The best solution to almost every Ubuntu "I get no/bad sound" problem is to forget the internal sound card and go USB. 

Over the years, I have had occasion to struggle getting speakers and microphone working using the internal card in notebooks and desktops. In every case the best solution was to use a "skype compatible" USB headsets with detachable USB modules (in other words headphone and microphone actually use regular TRS connectors that plug into the USB dongle). Plantronics and Sennheiser make these. 

The USB sound is truly plug and play. The good thing is that with the headset is working you can then use the TRS connectors to any speaker or microphone you want. 

Now I can get speakers, headphones, and mic working with Ubuntu on any USB equipped box - no fuss, no muss.

---

### Post by acampbel on 2009-03-29
I have a Plantronics headset I use with Skype on XP with no problem, but I can't get any sound out of them with Ubuntu 8.10.  They use USB, just as you described.   The Alsa mixer seems to recognize the headphones, but there is not sound, ever.:(

---

### Post by pewterbot9 on 2009-03-30
This is what worked for me, re. USB speakers:



VLC Media Player settings:



tools > preferences > audio



Change Output type from default to:



UNIX OSS audio output



and Device to:



/dev/dsp1



or 



/dev/audio1



(or try "2" instead of "1" for either option above)



YMMV. There is more than one solution, see this page:



USB Audio / Speakers with Ubuntu Linux

[http://www.michaeldolan.com/258](http://www.michaeldolan.com/258)

---

### Post by acampbel on 2009-03-30
Thanks a bunch!  You got me on the right track!  

For Ubuntu 8.10 with Gnome, things are a bit different, just in case someone else needs this solution:

System/Preferences/Sound

I set sound playback for Sound events, Music and Movies and Audio Conferencing to 
C-Media USB Headphone Set USB Audion (OSS)

and the Default Mixer Tracks to 

C-Media USB Headphone Set (Alsa mixer)

Important safety tip.  If you have, like me, had the volume maxed out on your headphones and Alsa mixer, you may want to turn them closer to very low before pressing the Test button.  Your success will otherwise be more painful that necessary :)

Again, Thanks a bunch!

---

### Post by acampbel on 2009-03-30
ooops, spoke too fast.  I was so excited about getting sound, I did not notice that only my headphone volume control worked.  So far, I've not been able to get the Also mixer to control the sound volume, just in case someone is trying to follow my directions.

---

