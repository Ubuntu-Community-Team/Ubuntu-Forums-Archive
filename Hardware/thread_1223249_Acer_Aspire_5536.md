---
title: "Acer Aspire 5536"
date: 2009-07-25
forum: Hardware
---

### Post by LemurApocalypse on 2009-07-25
I was surprised that this machine was relatively well-supported by Ubuntu, but it still has some issues. The microphone doesn't seem to be detected at all; Sound Recorder doesn't find it, anyway (the only option is "Capture.") How would I go about configuring it?

The other issue is that the headphone jack doesn't seem to be being used at all - plugging headphones or speakers into it has no effect. No sound comes through them, and the laptop's main speakers are still used.

I might have issues with the webcam as well, but I haven't gotten around to testing it yet. It was mentioned in System Tests's log, so I'm assuming it was detected.

Thanks!

---

### Post by fouserge on 2009-07-26
I just got the same laptop (if it's the 5536-5883).

I eventually got the mic to work, I think it was eventually done by messing with the settings. Took a few hours and really not sure what go it right. It is still extremely quiet though and almost not really worth it.

I haven't gotten around  to trying to get the ports on the side so not sure if they work.

One of my biggest issues now is that the 5 in 1 media card reader isn't working.

---

### Post by LemurApocalypse on 2009-07-26
Camstream detects the webcam. Can't seem to get an actual video feed from it though.

@fouserge, any pointers for which settings to mess with?

---

### Post by fouserge on 2009-07-26
Ok well I've rebooted since my mic was working and now it's not picking it up again. I've been testing it through skype and sound recorder.

My webcam worked with no tweaking. Both Cheese and Skype use it with no problems.

 Now I gotta get back to figuring out what happened to the mic. I think it has to do with setting the capture device as "Front Mic" and setting the volumes right.

---

### Post by LemurApocalypse on 2009-07-26
Sure enough, Cheese picks up the webcam fine. I've still had no luck with the mic or the other audio issue though. :(

Acer seems to be really bad about documenting their hardware and releasing drivers, even on Windows.

---

### Post by takvera on 2009-08-20
I just bought one of these Laptops and discovered I had no sound from the Headphone socket. It has taken me a while playing around with the Alsa mixer controls using the HDA ATI SB device.

The Front speaker control adjusts volume on the onboard speakers. The Surround Control adjusts the headphone/external speakers volume control.

Haven't tried using the onboard mic yet.

---

### Post by JK3mp on 2009-08-20
I had the exact problems with my acer, no sound through headphones, and no video but as u said got it through cheese. Also no mic work. I believe i was able to get drivers for it. Google around the forum cause i know i followed a post on here.Can't remember what i did exactly was like 10 months ago. Sorry.

---

### Post by fouserge on 2009-08-22
> **takvera said:**
> 
The Front speaker control adjusts volume on the onboard speakers. The Surround Control adjusts the headphone/external speakers volume control.

Thanks for the find, thats really helpful.

---

### Post by apuglisi on 2009-09-26
Hello my friends. After a big headache with the microphone thing, I've got it to work.
My notebook is an Acer Aspire 5720 Z and this is what got it working today:

Add the following lines to the configutaion file:  /etc/modprobe.d/sound


# Code to get mic working:
options snd slots=snd-hda-intel
# u1Nb.Z0J4Co96n9E (ICH8 Family) HD Audio Controller
alias snd-card-0 snd-hda-intel
options snd-hda-intel model=auto

after rebooting, the soundcard was completely recognized with internal microphones and all.
I really hope this helps you.

---

### Post by fouserge on 2009-11-01
Karmic has fixed just about every problem I had with this computer. Although I haven't gotten around to testing the microphone. It has even fixed some of the inconveniences I had before but just accepted.

---

