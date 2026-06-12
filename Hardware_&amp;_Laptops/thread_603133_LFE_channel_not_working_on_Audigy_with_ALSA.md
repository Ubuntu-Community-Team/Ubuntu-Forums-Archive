---
title: "LFE channel not working on Audigy with ALSA"
date: 2007-11-04
forum: Hardware &amp; Laptops
---

### Post by malaeum on 2007-11-04
I am trying to get ALSA properly setup here on my Audigy (original, Audigy 1 if you please). I am running Ubuntu 7.10 and haven't manually edited any configuration files, at least not yet, I want to see if there is a "Ubuntu-ized solution". I have been a Gentoo user for years and I am very impressed with Ubuntu. I have been falling back on methods that are outdated though and as a result have been doing too much work to fix issues. Anyways.... back to the issue at hand. I have an Audigy card here and its working great, but the LFE channel is not functioning properly. If I am not mistaken that is the .1 part or the subwoofer.  when I run ```
mmschnei@benzene ~ $ speaker-test -Dplug:surround51 -c6 -twav
``` everything except the LFE channel produces sound it the correct location. I believe that the LFE channel is driven through the same plug as the center channel, which is functioning just fine, so I don't think its a connection issue. The card is hooked up with three 3.5mm stereo cables to a Logitech  Z5500 speaker system. The tuner box that it comes with is currently set to "6 Ch Direct" mode so I would assume that it is not doing much (if any) signal processing and/or mixing of the sound. When I use either kmix or alsactl (in a terminal) I am able to control the volume of each set of speakers using the PCM channels not the non-PCM ones though. IE, PCM Front, PCM Center, PCM Rear, work for adjusting the corresponding speakers, however the LFE adjustment does nothing to solve my lack of sound through that channel. When I use the"Front" "Rear" "Center" or "LFE" channels (not preceeded with PCM) no changes are made to the corresponding channels. I have played around with the different switches available (Tone, Audigy Analog/Digital Output Jack, External Amplifier....) and have had luck. Also of note is that I find it odd that my front left and right channels do sound quieter than the rear and center channels by a decent ammount. I am able to correct this in alsamixer by turning the rear and center channels down about 20% lower than the front, but I am not sure why this would be required, something does not seem right to me here.

Not sure if anyone is able to help but I would greatly appreciate it. I searched the forums for about 30 minutes before posting this and haven't come across anything terribly meaningful yet, I however do apologize if this solution has been covered already. 


Thank you very much in advance for any and all help!

---

### Post by malaeum on 2007-11-05
Anyone have any ideas?


Seems like I am using a very common card/driver. I'd hope that this is supported...

---

### Post by malaeum on 2007-11-05
Guess not.   =\

---

### Post by Master_Rex on 2008-06-07
same problem here man...i have the exact same configuration as you and I hear a very "blurry" voice when it comes to the LFE channel...

---

