---
title: "sb0090 audigy with live drive optical out -HELP"
date: 2007-05-04
forum: Hardware &amp; Laptops
---

### Post by lawson23 on 2007-05-04
I have installed mythtv using the this guide with Feisty Fawn
[https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend](https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend)

I also previously had installed myth using the same type of guide but for edgy.

In either version I am having trouble with getting my sound card to output digital audio through a optical cable.

I have a soundblaster Audigy SB0090 with the live drive.  The live drive is where the optical out is.

I have tried everything I can think of and find to do.  I can get stereo audio out the back of the sound card but I have not been able to get the optical to work.

1. Issue could be in Ubuntu sound setup
2. Issue could be in Mythtv sound setup

Is there a way to test sound outside of Myth through my optic cable?

---

### Post by superm1 on 2007-05-04
Your going to have to play a little with the switches in alsamixer (over command line)  There are some switches for analog/digital out.  Also for IEC958 out.  In myth, you will need to see which devices you are assigning.

---

### Post by lawson23 on 2007-05-06
Ok Here is the full story
I had stardard audio out working through drapper I reinstalled to Fiesty and now I can't get sound at all.  When writing the first post I thought I would obviously get my standard audio back without complications.

I have everything in alsamixer turned on and up.

Here is my.
```
aplay -l
```
```

**** List of PLAYBACK Hardware Devices ****
card 0: Audigy [Audigy 1 [SB0090]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: Audigy [Audigy 1 [SB0090]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Audigy [Audigy 1 [SB0090]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

In myth I have choices of:
output device
/dev/dsp
/dev/adsp
ALSA:default

passthrough output device:
ALSA:iec958:{AES0 0x02}
default

I don't remember what I had available to me with my drapper install.

I take it I will have to type in the device I want to use in one of these settings.

---

### Post by superm1 on 2007-05-06
Okay,
Here is what I am doing for Coax output on my SB Audigy2.  Should be the same for optical output.

**1) I created a file ~/.asoundrc with these contents**
```
pcm.!default {
        type plug
        slave {
                rate 48000
                pcm "spdif"
        }
}

```
**2) Opened up alsamixer.  Here is the results of it.**
External amplifier: On
Analog Digital Output Jack: On
IEC958 Optical Raw: On
**3) In Myth:**
Audio Ouptut Device: ALSA:default
Passthrough output device: Default
Checked Enable AC3 to SPDIF passthrough
Checked Enable DTS to SPDIF passthrough
**4) Xine settings**
The only setting I changed was:
```
audio.output.speaker_arrangement:Pass Through
```


Now all of that above gets me this functionality: 
All AC3 or DTS stuff in both myth (HD Recordings) and xine (DVDs & Hidef movie files) gets passed through.  My receiver then handles all the decoding of that.

Everything else is forcibly put through the coax as raw PCM audio.  My receiver lights up a little PCM indicator when handling this stuff.


If this doesn't immediately work for your optical audio, you will probably need to flip a few things in alsamixer yet.  I say do it with coax initially, and once you are sure it works with coax how you want, you switch to optical.  

Also - please do post back to this thread what you had to end up doing for making optical work that was different than what I have above (if anything does have to be different).  I've been meaning to post this information for others for quite some time.

---

### Post by lawson23 on 2007-05-07
From ALSA
[http://www.alsa-project.org/alsa-doc/doc-php/asoundrc.php#aso](http://www.alsa-project.org/alsa-doc/doc-php/asoundrc.php#aso)
> The asoundrc file is typically installed in a user's home directory

	$HOME/.asoundrc

and is called from

	/usr/share/alsa/alsa.conf
It is also possible to install a system wide configuration file as

	/etc/asound.conf

When an alsa application starts both configuration files are read.

Below is the most basic definition. 


First still no luck in doing as suggested but using the above /etc/asound.conf
I also didn't make any changes to Xine as I couldn't locate where to add this.

1. Do I need to do something in the alsa.conf to call this file?

I will try it tonight using the ~/.asoundrc as requested.
1. This should be the user home dir that runs MYTHTV correct?
If I don't see a response  this is what I'm going to try.

---

### Post by superm1 on 2007-05-07
> **lawson23 said:**
> From ALSA
[http://www.alsa-project.org/alsa-doc/doc-php/asoundrc.php#aso](http://www.alsa-project.org/alsa-doc/doc-php/asoundrc.php#aso)


First still no luck in doing as suggested but using the above /etc/asound.conf
I also didn't make any changes to Xine as I couldn't locate where to add this.

1. Do I need to do something in the alsa.conf to call this file?

I will try it tonight using the ~/.asoundrc as requested.
1. This should be the user home dir that runs MYTHTV correct?
If I don't see a response  this is what I'm going to try.
I can't say much for the other files, because i don't know which override takes active.  Put it in the home directory of the user that runs mythtv, correct.  So if you have an automatic login going on as the mythtv user, it should go in that mythtv user's directory.  If its your normal user, then put it in their directory.

Xine can be done later, its only used for DVDs and movie files for me.  But it was much easier to do it rather than mplayer.  You can edit it from the xine gui (expert mode i think), or from ~/.xine/config.

---

### Post by lawson23 on 2007-05-07
Still a no go on the audio using coax or optical.

Question do you have the Premium drive addition with your audigy2?  I'm almost wondering if I should hook up windows to test the drive.


Second question not that it matters until I get sound but I was wondering.  The only difference between my setup and the guide that I can remember is I install VLC after I was done.  Problem is I can't decrypt dvd's.  I can play unencrypted.

Seems like I read libdvdcss2 wasn't needed anymore.  Am I wrong?

---

### Post by superm1 on 2007-05-07
For encrypted dvds, you still need libdvdcss2.  I'm not sure if this drive I have is a "premium" live drive.  Its white, and came with my Audigy 2 Platinum some 3-5 years back.

It has both optical and coax in and our on the front.  I can't think of anything else that I changed with my setup however.

---

### Post by lawson23 on 2007-05-07
Ok same here white bay unit.

I'm in the middle of installing the w32 codecs but I think I may see my audio problem (Power).  I will update as soon as I get a chance to test.

---

### Post by lawson23 on 2007-05-07
Boy do I feel stupid.

That was it.  No power to the drive.
Coax and Optical working 100%!

---

