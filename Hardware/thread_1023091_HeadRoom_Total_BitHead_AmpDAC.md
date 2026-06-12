---
title: "HeadRoom Total BitHead Amp/DAC"
date: 2008-12-27
forum: Hardware
---

### Post by maddog39 on 2008-12-27
Hey everyone,

I got this device for Christmas and it's recognised as a USB Audio Codec (just as it is in Windows) yet I cant seem to get ALSA to output any sound to it. I've gone into the volume control applet preferences and changed the output device to the BitHead and adjusted the levels in volume control accordingly for the device, yet all sound is still pushed through the onboard sound card and to the speakers. I've done some searching around but found nothing except a post from 4 years ago by the manufacturer confirming that it works under linux. It would be a real shame if this didnt work as its quite an expensive piece of hardware. For the record, im using Ubuntu 8.10.

Thanks!
-Alec

---

### Post by Nandro3 on 2009-01-11
I have a USB Dac I am trying to find a fix for as well and also have the same unit you just got.  Its nice, if you get it to work you'll enjoy it.

---

### Post by bonzini on 2009-04-28
I have a Total Bithead that works just fine, since Gutsy if memory serves.  Now happy in Jaunty.

Ok, there was one small gotcha :-)

The pulse audio / alsa / oss stuff needs a bit of fiddling.  So far what I've done in Jaunty is:

System > Preferences > Sound I have set Sound Events, Music and Movies, and Audio Conferencing sound playback to

Burr-Brown from TI USB Audio CODEC USB Audio (OSS)

Audio Conferencing Sound Capture is

ATI IXP rev 0 with ALC250 ATI IXP AC98 (OSS)

and Default Mixer Tracks is

ATI IXP (Alsa mixer)

I can't say for the moment that capture or mixer work right.

Then I fooled with the volume control, setting it to

Playback: USB Audio CODEC- USB Audio (Pulse Audio Mixer)

With these settings, I can listen to Rhythmbox or Songbird over headphones connected to the Bithead.

As I recall with Intrepid, getting Skype going was a bit umm taxing, though I think that was without the Bithead installed.  It seemed that getting Pulse and ALSA playing nice was challenging.

I hope this helps!

---

### Post by snapback77 on 2009-06-12
Similar problem with my new HRT music streamer dac.  Works with banshee not with the internet.  I dont hear the ubuntu drums logining on either. My Vista laptop works with it.  The internet music is much better than my soundcard.  Just cant get it to work with Jaunty Antelope.

---

### Post by Welly Wu on 2012-01-18
I bought a new HeadRoom Total BitHead in the middle of 2011. I have an ASUS N61JV-X2 notebook PC running Ubuntu 10.04.3 64 bit LTS. I connected the HeadRoom Total BitHead to a USB 2 port on my ASUS laptop and I see that it is powered on with the green light being turned on. However, I can not see the Total BitHead or USB Audio Codec in the Output tab within Sound Preferences in Ubuntu. When I try to play YouTube videos or Red Book CDs, it plays through my ASUS laptop speakers. How do I select the HeadRoom Total BitHead as my preferred output sound device so I can play videos, movies, and music through it using my Monster Cable Turbine Pro Copper Edition IEMs? Please help me out if you can. Thanks.

By the way, I called HeadRoom Corporation twice and they are not familiar with GNU/Linux at all. I might need to send a detailed e-mail message to one of their IT guys at HeadRoom for more detailed troubleshooting help. One of the HeadRoom guys told me to restart my computer in order to detect the HeadRoom Total BitHead while it is directly connected to a USB 2 port on my ASUS laptop as a possible solution. I will give it a try now.

---

### Post by Welly Wu on 2012-01-18
I just very quickly rebooted my ASUS N61JV-X2 notebook PC and Ubuntu 10.04.3 64 bit LTS recognized my HeadRoom Total BitHead and I am able to use it to play YouTube videos, movies, and music with my Monster Cable Turbine Pro Copper Edition IEMs and Audio Technica ATH-W5000 Raffinato headphones using 1/8" to 3.5mm adapter.

---

### Post by Welly Wu on 2012-01-19
My HeadRoom Total BitHead sounds wonderful in Ubuntu 64 bit GNU/Linux with my Monster Cable Turbine Pro Copper Edition IEMs! It works!

---

