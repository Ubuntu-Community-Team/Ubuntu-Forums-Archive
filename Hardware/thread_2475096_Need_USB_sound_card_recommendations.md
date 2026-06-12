---
title: "Need USB sound card recommendations"
date: 2022-05-16
forum: Hardware
---

### Post by Autodave on 2022-05-16
The internal sound on this desktop is not the greatest.  Therefore, I am looking to get a decent external USB sound card.  I only need stereo....don't care about anything more than that.  I am wondering what decent ones there are out there that work with Linux.  Price: will go up to $100 US or even a little more.

Recommendations welcomed!

Thanks in advance!

---

### Post by him610 on 2022-05-16
Hey AutoDave,
I just did a search for "usb sound card for pc" and several possible candidates were displayed. Back in the day when pc sound cards were a thing to have, Creative Labs Soundblaster cards were the ones to have. I suppose they are still quality products. Amazon has one listed for $17.34. It might be worth your time to consider it. [https://www.amazon.com/Creative-Labs-70SB173000000-Sound-Blaster/dp/B06XBZ38ZJ/ref=asc_df_B06XBZ38ZJ/?tag=hyprod-20&linkCode=df0&hvadid=309833041189&hvpos=&hvnetw=g&hvrand=6019941900733511404&hvpone=&hvptwo=&hvqmt=&hvdev=c&hvdvcmdl=&hvlocint=&hvlocphy=9006731&hvtargid=pla-528312458572&th=1]("https://www.amazon.com/Creative-Labs-70SB173000000-Sound-Blaster/dp/B06XBZ38ZJ/ref=asc_df_B06XBZ38ZJ/?tag=hyprod-20&linkCode=df0&hvadid=309833041189&hvpos=&hvnetw=g&hvrand=6019941900733511404&hvpone=&hvptwo=&hvqmt=&hvdev=c&hvdvcmdl=&hvlocint=&hvlocphy=9006731&hvtargid=pla-528312458572&th=1")
Myself, I have never had any issues with onboard sound chips - they all seem to just work on all of my machines, both laptops and desktops.
Are you sure it is a hardware problem? Maybe it is a configuration issue. On each of my systems with a GFX card, I have 2 audio chips - one on the mainboard and one on the GFX card. Audio can be configured to use either chip.
Are you using headphones or an external speaker system as audio output? Some speaker systems may need an amplifier to get decent sound.

---

### Post by Autodave on 2022-05-16
I saw many on Amazon.....was really interested in people's opinions of ones that they have or have used.

I have sound on my RTX 2070, but that is only through the HDMI and the itty speakers in my monitor don't sound very good.  And I see no way of putting that output through my regular speakers.  Is there???

As for an amplifier, the sound is plenty loud enough, just not good quality.  My wife's machine has Beats Audio built in.  A set of Bose speakers hooked to her machine sound waaaay better than the same speakers hooked to my machine.  

I have a VERY cheap USB sound card.....I believe that it was less than $10......I have hooked that up to this machine and I actually think that it sounds a little better than the onboard sound.  That's why I was considering a good quality unit.  I record 18 channels of music every Sunday morning at my church and then bring that home and mix it here to use on a religious podcast.  So, a better quality sound would be quite helpful.

---

### Post by him610 on 2022-05-16
Errr, ok, thanks for the update. Sounds(no pun intended) as if you are way ahead of me in the audio category. Yes, your spouse seems to have a premium audio system - something to envy.
Do you have a vacant internal PciE slot that you could use for an internal audio card?
I assume you have tried to redirect the audio output from the GFX card to normal system outs using pavucontrol and alsamixer. I've never tried that - always just used the MB audio chip. I think I will try it though just to see if I can discover anything useful.

---

### Post by him610 on 2022-05-16
Well, here is what I have in my system.
```

hugh@b450m:~$ inxi -Axx
Audio:     Device-1: NVIDIA GK104 HDMI Audio vendor: Micro-Star MSI driver: snd_hda_intel 
           v: kernel bus ID: 07:00.1 chip ID: 10de:0e0a 
           Device-2: AMD Family 17h HD Audio vendor: ASRock driver: snd_hda_intel v: kernel 
           bus ID: 09:00.3 chip ID: 1022:1457 
           Device-3: Microdia type: USB driver: snd-usb-audio,uvcvideo bus ID: 3-2.7:7 
           chip ID: 0c45:6366 
           Sound Server: ALSA v: k5.13.0-41-generic 

```
pavucontrol gives me two choices - Device 1 and Device 2 as described above
I am using a Google Home (internet) Speaker and headphones for audio output. Whenever I Cast the audio to the Google Home Speaker the output to the headphones have no output.
When I am casting audio to Google Home Speaker, using pavucontrol I can select either Device 1 or Device 2 with no interruption nor any noticeable deterioration of sound quality.
When I am using the headphones, using pavucontrol when I select Device 1 I only get tinny sound through the monitor's cheap speakers, whenever I select Device 2, I only get sound through my headphones.

I guess we both learned something with this little exercise.
It is a solution. Maybe not the one you wanted, but it is an alternative solution.

---

### Post by Autodave on 2022-05-18
bump

---

### Post by Autodave on 2022-05-22
Gonna answer my own question!  Since no recommendation was given here, after much searching I settled on this one: 
**StarTech.com  7.1 USB Sound Card - External Sound Card for Laptop with SPDIF Digital  Audio - Sound Card for PC - Silver (ICUSBAUDIO7D)**


I love it!  Sound quality is fatastic!  Plug-n-play: Xubuntu recognized it instantly and switched right to it.   $39US.

---

