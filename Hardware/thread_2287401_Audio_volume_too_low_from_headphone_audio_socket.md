---
title: "Audio volume too low from headphone audio socket"
date: 2015-07-19
forum: Hardware
---

### Post by samuelsimon on 2015-07-19
I'm running Ubuntu 15.04 on a Fujitsu LIFEBOOK E752. Using the headphone audio socket the volume is very low even when set high. I've tried setting the volume above 100% but the output is still very low.

The internal speakers and bluetooth audio both function as I would expect. The headphone audio socket functions as I would expect when running Windows. 

Any suggestions appreciated. I hate it when something works on Windows and not Ubuntu.....

---

### Post by Bucky Ball on 2015-07-19
Get an audio stream going (play some music). Open Pulseaudio Volume Control. In the playback tab, check the device the stream is using for output. Check the output tab. Tweak around and see if you can fix. You should have it set to be coming out of the headphones.

---

### Post by samuelsimon on 2015-07-24
Thanks for the suggestions Bucky Ball. I thought this was what I originally tried. I can make sound could out the headphones but only at a very low level. There is an option to set the volume above 100% (150% or so) but this is still very quiet. Am I missing your point? Is there something else I should be trying?

---

### Post by Bucky Ball on 2015-07-24
Not that I can see, but you can also try the 'Configuration' tab in PAVolume Control and make sure that the correct devices is set there. I have HDMI first then under 'Built in Audio' I have 'Analogue Stereo Duplex'.

If what you tried was to play some music, open PAVC, check the Output and Playback tab to make sure you are using the correct device, then you are not missing my point. Now try the configuration tab and make sure the correct device is set under HDMI or Built in Device.

Don't go above 100%. If it's not audible at 100% it's not working. :)

Be careful when testing and tweaking also. If it suddenly starts working and you are set at 150% you could do some serious damage to your ears and/or equipment.

---

