---
title: "Microphone not working in Acer Aspire 2930"
date: 2008-11-16
forum: Hardware
---

### Post by madeinbrazil on 2008-11-16
I have the latest Ubuntu 8.10 installed on my Acer 2930, everything so far seems to work (sound, webcam, wifi, bluetooth) but the microphone.

The PulseAudio Applet shows nothing for recording. When I go to the Sound Preferences I have nothing related to microphone muted.

Any help on this issue?

---

### Post by madeinbrazil on 2008-11-18
bump

Any ideas on how I can check microphone settings to force my mic to be used / recognized?

---

### Post by jens83 on 2008-11-28
i also have acer 2930 and no mic. irritating, cause i have to use shitty vista to skype people..
please can somebody figure it out?
thanx

---

### Post by zdendour on 2008-12-02
hey guys,
I have now installed 32-bit version. Have you found out any possibilities to make the mic working? Also if I play music and insert my headphones the comp is still using the speakers. Any idea how to fix this?
Thanks a lot for any advice.

---

### Post by purba on 2008-12-24
Ubuntu don't automatic if you plug the headphone jack, speaker mute. You must manually turn off.

Open the properties of volume. There 2 volume slider, first one for speaker and the second is for headphone. If you want to use headphone and want the speaker mute, just slide down the speaker, vise versa.

---

### Post by madeinbrazil on 2008-12-25
@zdendour still no solution for me

@purba every other laptop I've used Ubuntu with this worked well, except this model.

---

### Post by Swerve1000 on 2009-01-07
I'm considering purchasing an acer aspire 2930, the ultra mobile 13" screen vversion.

Could you possibly tell me which version of the 2930 you guys are running and whether the only problem you are experiencing is with the microphone.

Many thanks!

---

### Post by Mikey_S on 2009-01-09
Hey there, experiencing the same problem with the Microphone... and it's the only problem i've occurred so far.

mine is the 2930 - 12", 2.0 GHz, 3 GB Ram, 250GB hard drive.

I Love the computer, i'm running it dual boot with Ubuntu and Vista Home Premium (which came pre-installed).

a few complaints:
- Speakers are pretty weak.
- A lot of junk pre-installed software with Vista
- Computer is a bit heavy compared to it's size (about 2 K.G)

But despite of the above, it's a bargain.
I love it's keyboard, design, wonderful screen and hardware.

I say go for it.

Has anyone found a solution for the Microphone problem?

---

### Post by laxaman on 2009-01-18
You can solve it using oss sound driver instead of alsa see this link :)
[http://nmlaxaman.blogspot.com/2009/01/acer-aspire-2930-ubuntu-sond-card.html](http://nmlaxaman.blogspot.com/2009/01/acer-aspire-2930-ubuntu-sond-card.html)

---

### Post by vigyani on 2009-01-18
Which is the Audio device use on your system? Is it HDA + Realtek?

---

### Post by laxaman on 2009-01-18
Its HDA

---

### Post by vigyani on 2009-01-28
OK Sound card is HDA

Which is the sound device? 

To find it out use Add/ Remove to install Device Manager.

Run it by Application --> System Tools--> Device Manager

Under Audio Device there is an entry for Sound Card
Under 'HDA Intel Sound Card' there is an entry 'ALSA Capture'.
In Summary Which is the Sound Device listed there?

Please get back.

---

### Post by barretr on 2009-02-19
See: [http://ubuntuforums.org/showpost.php?p=6721529&postcount=23](http://ubuntuforums.org/showpost.php?p=6721529&postcount=23)

---

### Post by dek_ugenk on 2009-09-10
> **vigyani said:**
> OK Sound card is HDA

Which is the sound device? 

To find it out use Add/ Remove to install Device Manager.

Run it by Application --> System Tools--> Device Manager

Under Audio Device there is an entry for Sound Card
Under 'HDA Intel Sound Card' there is an entry 'ALSA Capture'.
In Summary Which is the Sound Device listed there?

Please get back.

i found 2 ALSA Capture

1. ALSA Capture
    Device File : /dev/snd/pcmC0D0c
2. ALSA Capture
    Device File : /dev/snd/pcmC0D4c

what next?

please help

---

### Post by barretr on 2009-09-11
dek_ugenk, in a terminal:
```
sudo lshw -C multimedia 
```
Determine what module is being used under Configuration(i.e, snd_hda_intel).

Then:
```
sudo gedit /etc/modprobe.d/options
```
and add the following(replacing snd_hda_intel and model with your settings):

```
options snd_hda_intel model=acer position_fix=1 enable=yes
```
Save and reboot. Hope that helps.

---

### Post by solnyshok on 2009-10-14
I have Acer 2930Z and run KarmicKoala latest kernel 2.6.31-13 AMDx64. My internal mic, the one which is close to webcam, is not working. I get permanent noise, but no reaction to vocice. 

My computer has 3 jacks on the front panel: LINE IN, MIC, OUT: HEADPHONES/SPDIF. And has "Dolby Home Theater" branding. I guess this refers to SPDIF-OUT, which allows various outputs up to 7.1.
Audio chip is ALC888.

I have tried first with alsa 1.20(coming with KK), and later upgraded to the 1.21 (the latest build on alsa website, also latest on Realtek website, linux drivers). Tried various model options

model=acer
model=acer-aspire
model=acer-dmic
model=3stack
model=3stack-dig

I also played with all dials in the ALSA mixer. Enabling/maxing/unmuting etc. all dials for everything. Still, no voice recording from front mic. Model=3stack-dig seems supports most output modes (including 7.1).

Any idea what else I can do? Really not ready to switch to oss4.2 yet.

p.s. same mic works well in vista/w7x64.

---

### Post by solnyshok on 2009-10-14
I also looked around the web for any reference to Acer 2930z and found this [http://doc.ubuntu-fr.org/audio_intel_hda](http://doc.ubuntu-fr.org/audio_intel_hda)

they have model parameters for various laptops. Suggestion for 2930z is 

options snd-hda-intel model=auto position_fix=0

but seems that internal mic is not working either ((micro interne non fonctionnel)

---

### Post by solnyshok on 2009-10-14
So, I tried the model=acer-aspire-4930g
and now my mic is peaking up my voice, but very soft, almost silent. I can max volume and amplification, and then hear my voice, but background noise is terrible.

---

### Post by solnyshok on 2009-10-14
Looks, like my mic is ok now. Not that I changed much vs. my last post. But, I had time at home to play a bit with alsa mixer, gnome alsa mixer, and gnome sound preferences and to record my voice 3 dozen times without looking like an idiot to my colleagues, and now I found a combination of settings that gives bearable speech in skype. Recording from "gnome sound recorder" is still moderately noisy, but skype employs decent noise suppression algorithms, I was surprised afer making a test skype call.

So, my settings (in addition to mentioned above model=acer-aspire-4930g)

choose StereoDuplex mode
enable mic2 and mute mic1,
set amplification (mic boost) to around 70-75%,
choose mic2 as input for recording programs.

---

### Post by barretr on 2009-10-14
solnyshok, try the solution in this thread: [http://ubuntuforums.org/showthread.php?t=927270&highlight=internal+mic]("http://ubuntuforums.org/showthread.php?t=927270&highlight=internal+mic")

Failing that, you could try an external mic.

---

### Post by solnyshok on 2009-10-14
thank you barretr. that thread advises to compile latest alsa drivers and set model=acer, which did not work for me earlier. model=acer-aspire-4930g is the parameter that makes internal mic work.

Now I my internal mic is ok. Thank you for your help.

---

