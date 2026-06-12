---
title: "Laptop Microphone Problems"
date: 2010-03-18
forum: Hardware
---

### Post by ozanamn on 2010-03-18
Hey,

I have a Compaq Presario CQ61, 

Im running 9.10 and 

I had to do the command below to get my speakers working. I hadn't noticed until i tried to use skype that the microphone isn't working.

Iv search around and all people are saying is try the command below which I have already done to fix the speakers. 


> 
sudo gedit /etc/modprobe.d/alsa-base.conf
At the end of the file, add these lines

> 
options snd slots=snd-hda-intel
options snd-hda-intel model=hp-hdx
alias snd-card-0 snd-hda-intel
options snd-hda-intel enable_msi=1

If you want any outputs or logs let me know.

Cheers,
Oz:D:D

---

### Post by I8NY on 2010-03-18
okay by the looks of your file editing you have alsa audio driver and you have to edit the mixer to get the microphone working.  If you don't have the GUI mixer I would get it by running    	   	 	 	 	 	[FONT=monospace]"[/FONT]sudo apt-get install gnome-alsamixer" 	and a ALSA mixer app should be under 	 audio & video.  Open the mixer and there should be a column called "capture"(maybe 2) and a check box called "Rec." check it and raise the volume.  The Mic should work now.

---

### Post by ozanamn on 2010-03-23
Hey sorry it took so long to get back and your quick response..

i tried all that and changed it around a million different ways and and still no luck...  am i all out of ideas?

Oz

---

### Post by I8NY on 2010-03-24
well i don't know what else to do i am not a pro at editing the config file directly so I hope you get some one who is a pro at solving this.  You might want to try reinstalling the audio driver.

---

### Post by gradinaruvasile on 2010-03-24
Ok, try this:

1. PulseAudio GUI:

Right click on the volume icon, click sound preferences, go to the hardware tab.
Here you have a "Choose a device to configure" section:
 - Select the internal card (probably the only one) and make sure its profile is "Analog Stereo Duplex"
 - Go to the Input tab and see if you have a sound input device listed, make sure its not muted, turn up its volume to about 3/4, tap the laptop beside the keyboard to see if you have any input signal. If not, try selecting the other connector (You have Mic 1 and 2 or Microphone and Line in).

2. Alsamixer:

If the above does show a microphone and there is still no input signal, open a terminal and type

alsamixer

Press tab (cycles views) to go to the recording view and post a screenshot of it here so people who know their way around have their chance to help you.

Make sure you enlarge the terminal so that all items to be visible - keep in mind, the CAPTURE view is of interest here, the first default view is playback, not interested in it ATM. Also, the "all" view is confusing, it is not helpful at all.

Other than that, try selecting (in the capture view) the input sources (the volume indicators with 4 horizontal lines below them) - select with right/left, toggle capture with space - volume levels with up/down. These settings apply on the fly.

---

### Post by Finn bjerke on 2010-12-08
Try a bluetooth solution if the problems persists. Nokia BH-105 works well and wireless with skype.

---

