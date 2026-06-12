---
title: "Sound?  OFF! - Yes, no sound."
date: 2009-08-23
forum: Hardware
---

### Post by catnip_X07 on 2009-08-23
Been working on a sound problem, as I am new to welcoming Linux.  Followed a lot of guides and so far no luck.  Sound is HDMI from card1 on an integrated motherboard.  (card 1 is HDMI ; card 0 is normal sound through sound jacks?)

Here is the oddities of the problem:
When I boot up and when loading screen appears, I believe I have sound as my audio receiver is picking up a signal (via HDMI).  Once the desktop appears, sound signal is lost.  I can test the sound card and I hear a tone, which makes me believe sound is working or at least a connection is established.  I can use rythmbox and hear sound through that.  Any other application, and no sound at all.  IF I manually select an audio driver in an application (SMPLAYER), I can get sound although video quality is a bit subpar.

Here is what I think is happening, and maybe someone can concur.  Whenever the desktop is loaded after booting, somehow card 0 is being loaded instead of card 1.  When I manually tell an application what to use, such as guiding the application to use a sound driver, is when sound works.  

If my assumption is correct on the sound problem, is there anyway to disable the system from loading card 0 and making card 1 the default sound source?  If so, HOW?  IF this is not my problem, what is my problem and how do I correct?

Thank you

---

### Post by Cresho on 2009-08-23
yes there is but you need to tell us what operating system you are using

---

### Post by catnip_X07 on 2009-08-24
The os is ubuntu 9.04

---

### Post by maximilion on 2009-08-24
Do you have a volume control icon in your task bar? If so, double-click it and check the sliders. If not, right-click the task bar and add one.

If the problem is only playing .mp3 / no sound in youtube clips, it's a missing codec problem. I have a hard time believing the installer wouldn't get flash-nonfree for your browser automatically, but if so get it with Synaptic.

For mp3 I just double-clicked an mp3 file and my media player (totem) got the nonfree codecs "automatically".

---

### Post by catnip_X07 on 2009-08-24
No system sounds are played either. Don,t think it's a codec issue. Tried all the slider tricks in volume control to no avail.

---

### Post by catnip_X07 on 2009-08-26
I guess I may not be the only one stumped on this?  
Cresho may have had a resolution for this....?!

---

### Post by Cresho on 2009-08-26
open up terminal

#alsamixer

tell us what it says about your card, chip.




now use your tab key and select all.

use your arrow keys and look for

you can select a volume with the arrow keys left or right.  if you choose a volume, use up and down keys to change levels.

What i need you to look for is something that actually turns on your audio.  I have a few fixes up my sleeve but i need to know in general what is supported.

on my system for example, i select "audigy A" switch (light-on green indicates on) which i have on.  above in item it says analog digital output jack.  this is the type of switch i am wondering if you have on your system.  is it analog/digital off or on?

after we resolve this or if it gets resolved, I can tell your system to force boot and resolve any issues.

---

### Post by tommcd on 2009-08-27
> **catnip_X07 said:**
> 
If my assumption is correct on the sound problem, is there anyway to disable the system from loading card 0 and making card 1 the default sound source?  If so, HOW?
Is there an option in the computer's BIOS to disable card 0 and make card 1 the default sound source? If so, then try that.

---

### Post by Cresho on 2009-08-27
could be  an audio priority but we can get to that after.  I need to see if his mixer sees the unit like the post i made right above yours as I mentioned.

---

### Post by catnip_X07 on 2009-08-27
Out of town at the moment, but from what I remember is that nothing was muted (if that is what you are referring to?).  I did alsamixer card0 and card1 and all sound options are active (green light).  I figured they were not muted as I can get sound on some applications when I reference the audio driver.  
It may be the audio priority you mention Cresho.  What are your thoughts on how to set the priority?  I only know of blacklisting card 0, which didn't work.

---

### Post by Cresho on 2009-08-30
It doesnt matter if its muted or not, there is a switch that tells your card to go on.  This is what I am looking for.  I'm starting simple and then we go for the harder stuff.

---

### Post by catnip_X07 on 2009-08-30
ok.  Typed alsamixer and came up with: 
card: HDA ATI HDMI
chip: ATI ATI RS690/780 HDMI
View: [ALL]
Item: IEC958

Only one box at the bottom with two zeros with green background.  Can't do anything with it (up, down arrow, etc).  

I open rhythmbox and can hear sound ; smplayer with ATI HDMI selected for audio driver and have sound.  Everything else, no sound.  

Is there anything else I should do?

---

### Post by vektsilver on 2009-08-30
one thing you may want to watch out for is in the audio mixer there is sometimes a resource that can be toggled to switch between analog out or digitial out.

I experianced this on my laptop and my desktop ( sound blaster audigy2 ) the default for the setting should always be analog but what happens is sometimes it comes up digital out and that effectively shuts off any normal analog sound hence " no sound " unless connected with digital to a digital reciever.

just go into the mixer with the appropiate device selected and look in preferences for anything labeled analog/digital output jack.  If it is not checked check it then go into the mixer under the switches tab and  you can then toggle it to see if that helps.

---

### Post by Cresho on 2009-08-31
just like the guy above says.

anyway, do a

#asoundconf list

in the terminal and tell me what you see?  we may need to force boot the correct sound device which is not hard.  I just need to see this command output im asking for.

---

### Post by catnip_X07 on 2009-08-31
Took me a while...realized when I played with this last night, I blacklisted a few items and result was nothing when I typed asoundconf list

Here are the results after deleting my added items to blacklist.


Names of available sound cards:
SB
HDMI

---

### Post by Cresho on 2009-09-01
im going to assume you are using hardy.

install this one


if you want to try a gui use this one
#sudo apt-get install asoundconf-gtk

then you can select your soundcard in 

system->preferences->default sound card

you select that and select the audio you want to try. now you play with your audio mixer and software to see whats going on.

if you dont want to play with a gui, you can do it in terminal like for example you have checked for your audio.

#asoundconf list

choose one audio and execute this

asoundconf set-default-card SB

or

asoundconf set-default-card HDMI



if you create  a script, you can do this and place it in sessions to force your card as primary.

```
#!/bin/bash
sleep 10 && asoundconf set-default-card HDMI;
```


select one card and play with mixer and audio.  if not, try other card and repeat your process.

if this isnt working, you will definetly need to check the audio hardware.  What is it?

---

### Post by catnip_X07 on 2009-09-01
got sound when testing via GUI by selecting the HDMI device.  Sound was clear.  asoundconf set-default-card HDMI did not work apparently.  

Same situation as earlier though.  no applications have sound except rhythmbox and smplayer when I select the audio driver.

---

### Post by catnip_X07 on 2009-09-07
Re-installed the whole OS.  nothing.  seems worse than before.

---

### Post by Rockbuster on 2009-09-08
I just had the exact same issuie today, it took me a long time to figure out. it sounds like you've got 2 sound chips (I had 3...yeah, I'm crazy). There's an elegant way to do this - simply disable the default sound card and the HDMI one becomes the primary sound chip by default.

open your terminal and type
```
sudo lsmod | less
```

Near the bottom of the list, you should see a few lines beginning with "snd_" - those are your sound chips. I had things like "Snd_intel8x0" and "snd_emu01k." The sound card you want to use (the one you're not disabling) should have ATI somewhere in its name. Copy the ID of the other sound card (the one you're disabling), or write it down somewhere.

Open your file browser and go to /etc/modprobe.d/ and open the "blacklist" file (I had to open it with sudo). At the end of the file, add these lines:
```
#Disable the analog soundcard
blacklist (soundcard ID)
```

Once you reboot, your HDMI sound chip will be default, since it's the only sound chip enabled. Enjoy the sound :popcorn:

---

### Post by catnip_X07 on 2009-09-08
I think this is the route I need to go, rockbuster.  Here is what I got from aplay -l
card 0: SB [HDA ATI SB], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


This is what I got from your lsmod | less (edited):
snd_hda_intel         435636  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
cx25840                35632  0 
lirc_mceusb2           20100  0 
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ppdev                  15620  0 
k8temp                 12416  0 
pcspkr                 10496  0 
shpchp                 40212  0 
lirc_dev               19892  1 lirc_mceusb2
cx23885                94244  0 
i2c_piix4              18448  0 
snd                    62628  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm


Nothing that appears to be too detailed like you describe.  Anyway to blacklist card0?

---

### Post by catnip_X07 on 2009-10-06
SO....I have given up on this for now.  After a few more alterations, I finally got NO SOUND AT ALL.  Not even during tests.  I haven't even started on my hauppauge 1800 tvtuner card (what's the point if I don't have sound).  I think I may upgrade to 9.10 and see what happens.  I just don't understand why this is so difficult.  So far, I haven't gotten to 
"linux just works"   

As a person who wanted to explore linux via UBUNTU, this is not a good start.

I do want to thank everyone so far for their help.

---

### Post by catnip_X07 on 2009-11-13
SO....9.10 works for sound coming through "normal" sound speakers (i.e. not hooked up to HDMI routed to a receiver).  This is one BIG improvement than earlier.

---

### Post by catnip_X07 on 2010-01-05
Finally got around to hooking up HDMI to my surround sound system.  Works great.  Looks like 9.10 did the trick.

---

