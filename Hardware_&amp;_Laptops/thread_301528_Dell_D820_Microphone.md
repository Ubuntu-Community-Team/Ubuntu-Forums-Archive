---
title: "Dell D820 Microphone"
date: 2006-11-17
forum: Hardware &amp; Laptops
---

### Post by oliwally on 2006-11-17
I have installed 6.10 Kubuntu on my Dell D820 and all works well, except that the built-in microphone doesn't appear to be working. Nor have I had any luck when plugging in an external microphone. How do I fix this?

In the end I'd like to be able to use Skype and Audacity (both already installed using Automatix). Skype works, except no microphone, and Audacity crashes when I try to record with it. What do I need to do?

---

### Post by psych-major on 2006-11-17
I am running Kubuntu 6.10 on my D820, and I am having the exact same problem, except that in my case, Audacity works fine, and I get valid input from the built-in mic.

I had to toggle the setting between mic and line-in via kmix, and doing so requires closing and restarting Audacity.

However, even after this, I have no luck in Skype. I have tried both alsa and oss, but same result, i.e. I have sound, but no mic. ](*,) 

I'm searching some other forums, so if I find something, I'll post it back here, too.

---

### Post by psych-major on 2006-11-17
I got it!!!

In alsa, you need to enable full duplex sound.
Then, in Skype, make sure to select alsa as the default sound device. Mine had defaulted to oss.

I did this in the KDE sound system config, but if you're using gnome, I'm sure there's something similar there. 

Good luck, and let me know how it turns out!

---

### Post by oliwally on 2006-11-17
> **psych-major said:**
> I got it!!!

In alsa, you need to enable full duplex sound.
Then, in Skype, make sure to select alsa as the default sound device. Mine had defaulted to oss.

I did this in the KDE sound system config, but if you're using gnome, I'm sure there's something similar there. 

Good luck, and let me know how it turns out!

Thanks for your quick reply. Unfortunately those suggestions did not work for me. I also use KDE 6.10 and have switched the sound system form Automatic to ALSA, but I still cannot get the microphone to work. I've reinstalled Audacity and it no longer crashes (for now) but I can get nothing through the microphone. I've also tried KRec, but same result. 

Can anyone help to make the microphone go?

---

### Post by oliwally on 2006-11-18
> **oliwally said:**
> 
Can anyone help to make the microphone go?

Alsamixer has a spot for the mircrophone, but I cannot enable it with either 'M' or the Spacebar, nor is there a volume bar that can be adjusted up or down. It appears that somehow the Kubuntu configuration is not enabling the microphone. Please help.

---

### Post by oliwally on 2006-11-19
Bump. Please help. Where do I start to find out what's wrong?

---

### Post by paul.o on 2006-11-19
Same problem but now I can make skype calls

as per previous post make sure that duplex is on

Open kmix and under the input tab make sure that mic has the green mute spot highlighted at the top then check that both mic and capture have their red input dots on and their volume sliders are turned up (iec958 playback also has its red input dot on). In the switches section the only one I have highlighted is mic boost (+20db)the other options I have here are

surround jack mode = shared
mic select = mic1
iec958 playback source = pcm
mono output select = mix
channel mode = 2ch

hope this helps

---

### Post by oliwally on 2006-11-19
Thanks so much for helping out paul.o.

For some reason my kmix menu doesn't have all those options. Under the Switches section there is very little: one dropdown menu for Input source, with the only option being Mic. An there is a radio button above the word IEC958. This radio button will turn off or yellow when clicked. In the Input section I have two sliders - Capture and Capture Mux. The radio button below these will turn off or red only and there is a red, paused volume symbol above the capture slider.

Hmmm. It's beginning to look like something didn't install correctly or recognize the microphone. I don't know what to do about it - my linux knowledge isn't big enough.

---

### Post by oliwally on 2006-11-20
Still needing some help with my D820 microphone please.

---

### Post by oliwally on 2006-11-22
Bump;)

---

### Post by oliwally on 2006-11-23
I will donate a kidney to the person who helps me solve this. :D

---

### Post by ilushkin on 2006-11-25
i have Inspiron  E1505 and experienced the same problem. Then all of the sudden I got it working by messing with the Gnome's Volume Preferences.

---

### Post by karthikp on 2006-11-26
Follow this for Kubuntu (6.06):

1. Use System Settings > Sound & Multimedia preferences to make sure you have Full duplex enabled (Look in the Hardware tab). Audio Device is set to 'Autodetect'.

2. Use KMix to make sure that 'Record' is turned on for the microphone device. You may have to pick the in-built/external microphone from a drop-down menu in KMix.

3. In Skype, set sound system to Alsa and set the Sound In option to the same microphone you enabled in KMix.

4. Profit!!! :p

---

### Post by paul.o on 2006-11-26
Sorry, I should have made it clear that I had the sound problem on my desktop machine, I was hoping that the way I resolved my problem would be of help to you

again apologies

---

### Post by oliwally on 2006-11-26
Thanks so much folks for helping out, but my kidney is safe for now. Still no luck.

> Follow this for Kubuntu (6.06):

1. Use System Settings > Sound & Multimedia preferences to make sure you have Full duplex enabled (Look in the Hardware tab). Audio Device is set to 'Autodetect'.

2. Use KMix to make sure that 'Record' is turned on for the microphone device. You may have to pick the in-built/external microphone from a drop-down menu in KMix.

Yes, I've done all that as much as possible, but in Kmix I don't even have the microphone options. It seems to be missing something. I'm starting to think that the microphone somehow didn't get recognized during installation. Should I reinstall ALSA or something like that?

---

### Post by oliwally on 2006-11-27
Bump ](*,)

---

### Post by peachy on 2006-11-27
I have the same problem but mine is intermittently working.

Additionally in kmix above "capture" i have a red, paused volume control, and no option to set it green.

I just reset and restarted ALSA (there is no reason i though this would fix the problem, i just don't know much about it and it was all i could think of) and now i have sound in Skype, from the built in mic. Weird.

---

### Post by peachy on 2006-11-27
UPDATE: I have not made any changes to ALSA or skype and my mic stopped working again :-/

Retarting ALSA did not help, the mic was working in Audacity. I restarted skype and the mic worked again...

---

### Post by oliwally on 2006-11-27
> **peachy said:**
> I have the same problem but mine is intermittently working.

Additionally in kmix above "capture" i have a red, paused volume control, and no option to set it green.

I just reset and restarted ALSA (there is no reason i though this would fix the problem, i just don't know much about it and it was all i could think of) and now i have sound in Skype, from the built in mic. Weird.

Yes, that's what mine looks like, but my microphone never kicks in.... very strange.

---

### Post by oliwally on 2006-12-01
I'm still looking for some help with my laptop microphone issue please.

---

### Post by peachy on 2006-12-01
> **oliwally said:**
> I'm still looking for some help with my laptop microphone issue please.
Sorry to ask the question, but you have confirmed the mic works with another OS?

I'll admit mine is a little flakey, especially with Skype, but it does work.

---

### Post by oliwally on 2006-12-02
> **peachy said:**
> Sorry to ask the question, but you have confirmed the mic works with another OS?

I'll admit mine is a little flakey, especially with Skype, but it does work.

Yes, it works in WinXP, no problems at all.

---

### Post by oliwally on 2006-12-04
Ok, I've had some moderate success. When using Skype I've been able to get both the in-built microphone and a usb microphone (built into my webcam) to work by adjusting the audio options in Skype. The built-in mic worked when options OSS and dev/dsp1 were selected. The camera mic worked with ALSA and camera.

Weird thing is that dsp1 only showed and worked when the webcam/mic was plugged in. I can't get the computer's built-in mic to work any other way. 

Does anyone know what the problem may be?

---

### Post by oliwally on 2006-12-15
> **oliwally said:**
> Ok, I've had some moderate success. When using Skype I've been able to get both the in-built microphone and a usb microphone (built into my webcam) to work by adjusting the audio options in Skype. The built-in mic worked when options OSS and dev/dsp1 were selected. The camera mic worked with ALSA and camera.

Weird thing is that dsp1 only showed and worked when the webcam/mic was plugged in. I can't get the computer's built-in mic to work any other way. 

Does anyone know what the problem may be?

I'm still hoping for some suggestions to solve my problem please (see previous posts also).

---

### Post by peachy on 2007-01-10
Hi, have you tried psych-major's workaround here:
[http://www.justlinux.com/forum/showthread.php?t=120942&goto=nextoldest]("http://www.justlinux.com/forum/showthread.php?t=120942&goto=nextoldest")

That worked for me...

---

### Post by adam2007 on 2007-01-13
Hello All ,

I'm suffering from the same problem.

I'm running Ubuntu Edgy on my Dell 1405 laptop.
ALSA has recognized my sound card as HDA Intel.

Although I have perfect sound, my mic doesn't work at all. (Skype is all I need anyway)
It works fine in WinXP.

Thus far I've tried:
-Checking the volumes in ALSA Mixer ----- I can't change the volume of "Input Source" (not recognized?)
-Double clicked the volume icon and made sure that Mic is unmuted.
-re-installed alsa-base

but to no avail.

I'm as new as can be to Linux so if any response could be a detailed as possible it would be great.

Thanks in advance!

---

### Post by mixonic on 2007-01-13
Er, all should not be well using Edgy.  The headphone jack doesn't cut the internal speakers, for a start.

I compiled the newest alsa drivers from alsa-project.org and my output works fine, though I haven't tried the mic. Hm, at a quick try, the mic doesn't seem to work, but I havent tweaked alsa or anything.

You have everything working perfect for hibernate and suspend as well?!

---

### Post by Mguel on 2007-01-31
Had the same issue, but solved it with:

[http://forum.skype.com/index.php?showtopic=66544](http://forum.skype.com/index.php?showtopic=66544) by [RockHound]("http://forum.skype.com/index.php?showuser=105400")

> Hi everyone with mic problems,

to get your mic working, if skype is not recording from it, try the following:

- switch to the alsamixer view 'Capture' with TAB or start it with alsamixer -V capture -c CARDNUM
- make sure you have 'Mic' and 'Capture' sliders marked selected as CAPTUR ... to do this hit space

[IMG]http://www.martinadler.net/fileadmin/external_content/alsamixer_capture_settings.png[/IMG]

Once done, input should immediately be happening... [IMG]http://forum.skype.com/style_emoticons/skype/smile.png[/IMG]

Cheers,
Mguel

---

### Post by eggdeng on 2007-01-31
Some of these guys seem to have got a working mic on a Dell Inspiron.
[http://ubuntuforums.org/showthread.p...maTel+STAC9200](http://ubuntuforums.org/showthread.p...maTel+STAC9200)
The fix is to add

```
options snd-hda-intel model=ref
```

to
/etc/modprobe.d/alsa-base
Reboot for changes to take effect.

---

### Post by Bartisimo on 2007-02-21
Microphone problem on Dell D620 - Fixed!

Hello,

I have a D620 and my mic wasn't working.  I played around with alsamixer and it seemed to work.  I was using it with some tuners and it worked fine.  In a terminal type in alsamixer.
Then, turn up pcm (i dont know what it is correct me if im wrong), turn up capture and change soundso to mic.  (cautiously play aroung with these settings and monitor things through the recording monitor)  Hopefully this works - it did for me.

p.s. these settings might get reset on restart

---

### Post by eggdeng on 2007-02-25
Finally got that mic working following this thread.

[http://ubuntuforums.org/showthread.php?p=2210477#post2210477](http://ubuntuforums.org/showthread.php?p=2210477#post2210477)

---

### Post by ianfp on 2008-06-14
I'm using regular Ubuntu (not Kubuntu) 8.04, but on the off chance that this will help:  I went to the sound settings (System -> Preferences -> Sound) and under "Default Mixer Tracks" I chose "Capture" instead of "Capture Mux".  That got the mic working for me.

---

