---
title: "ac97 strange sound symptoms"
date: 2005-10-09
forum: Hardware &amp; Laptops
---

### Post by linuxgrrl on 2005-10-09
hi,
I have onboard ac97 audio and it is working (yay!).  
2 strange probs I really would like to fix though:

1. there seems to be no stereo.  This is a living room box, and the output travels over a y-cable to the composite right-left jacks on the TV.  My output should be in stereo then, yes?

2.  I am unable to control the volume at all ... even if I log in as root, even if I use alsamixer and try to control each channel individually ... if I turn the volume down to 0 on pcm it will mute, but other than that,  moving the sliders has no effect whatsoever.   

This is a mythtv box so I turned off the gnome "sound server" and used alsamixer and alsactl to pre-set the capture channel as needed for myth.  IN case it's relevent, the gnome volume control lists the following possible devices:  c-Media Electronics cMi9761 (OSS Mixer); SiS7012 (Alsamixer), and the two devices associated with my tv card.  
where should I look to try and get stereo and/or volume controls to work for my onboard sound? (even just a working alsamixer would be fine, I don't really need the gnome one to function)
thanks!!!
Mary

---

### Post by Eldon on 2005-10-14
> 1. there seems to be no stereo. This is a living room box, and the output travels over a y-cable to the composite right-left jacks on the TV. My output should be in stereo then, yes?

It depends what you mean by Y-cable.  Some y-cables are made to pipe a mono signal to 2 speakers.  If this is what you've used then both your speakers should be playing but you won't have stereo sound.  

I take it you're using a stereo sound blaster of some sort.  The jack that plugs into the sound card should look like the end of a set of headphones.  There should be 3 silver bands, if there's only 2 you've got a mono y-cable.  

I'm not sure what you mean by composite right-left jacks on the TV.  Could you elaborate?  
This is the cable style I'd recommend for most sound card to TV connections.  
[http://images.divx.com/guides/divxtv/stereo-minijack-to-rca.jpg]("http://images.divx.com/guides/divxtv/stereo-minijack-to-rca.jpg")
Note the 3 silver bands on the headphone-style end.  Is this what you're using?

---

### Post by linuxgrrl on 2005-11-03
Thanks for replying!   I just saw this yesterday.
[QUOTE=Eldon]
I take it you're using a stereo sound blaster of some sort.  The jack that plugs into the sound card should look like the end of a set of headphones.  There should be 3 silver bands, if there's only 2 you've got a mono y-cable.[/QUOTE]

dang, mine only has 1 silver band.  I guess I'm lucky it works at all :razz:    Now why would anyone sell a mono cable that connects two speakers?  Back to Radio Shack I go ....

[QUOTE=Eldon]I'm not sure what you mean by composite right-left jacks on the TV.  Could you elaborate?  
This is the cable style I'd recommend for most sound card to TV connections.  
[http://images.divx.com/guides/divxtv/stereo-minijack-to-rca.jpg]("http://images.divx.com/guides/divxtv/stereo-minijack-to-rca.jpg")
Note the 3 silver bands on the headphone-style end.  Is this what you're using?[/QUOTE]

My cable looks just like your photo except it has one silver band only. I admit I can't see the 3 bands in your photo, only 2, but mine is obviously not right.  Thanks for your help!

Now, can anyone tell me why I am unable to adjust the volume (other than mute/unmute?)  To recap, no matter which mixer program I use, the sliders have no effect on volume although they can mute/unmute channels. I don't want to use the gnome sound server because it conflicts with mythtv, so other ubuntu howtos based on the sound server don't seem to help.

Here's what I know about my hardware:

My motherboard manual says I have "AC97" onboard sound.  Ubuntu Device Manager says SiS is the vendor but the device itself is "unknown". 
The intel sound module is (sort of) working, and Gnome's volume control applet displays two device options: "C-Media Electronics CMi9761 (OSS Mixer)" and "SiS Si7012 (Alsa Mixer)." Both show the same symptoms: mute/unmute works, but sliders don't.

lsmod | grep snd returns:

snd_intel8x0 29984 2
snd_ac97_codec 64608 1 snd_intel8x0
snd_pcm_oss 47652 0
snd_mixer_oss 16768 3 snd_pcm_oss
snd_pcm 84872 3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer 23300 1 snd_pcm
snd 50276 6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore 9824 3 snd
snd_page_alloc 9604 2 snd_intel8x0,snd_pcm

So, can anyone point me toward how to adjust my volume?  I've re-checked the permissions on /dev/dsp and verified that my user is a member of all the right groups, but no luck so far.

Thanks!

---

### Post by lompolo on 2005-11-03
Test your microphone connection. My parents bought computer this year with ac'97 codec integrated to motherboard (ABIT as8 ). Microphone connection doesn't work in any of those motherboards (perhaps not in any of ac'97)

---

### Post by linuxgrrl on 2005-11-04
[QUOTE=lompolo]Test your microphone connection. My parents bought computer this year with ac'97 codec integrated to motherboard (ABIT as8 ). Microphone connection doesn't work in any of those motherboards (perhaps not in any of ac'97)[/QUOTE]

Thanks; unless I'm misunderstanding, I don't think that's it ... I have the same problem even when sound is playing frm the hard drive (i.e., no mic involved).  Anyone else can point me in the right direction?

---

