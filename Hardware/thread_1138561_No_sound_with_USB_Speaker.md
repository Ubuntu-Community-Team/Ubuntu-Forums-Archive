---
title: "No sound with USB Speaker"
date: 2009-04-26
forum: Hardware
---

### Post by eksatx on 2009-04-26
I am trying out Jaunty (9.04) on a Dell Dimension 4600.  I'm impressed with how far the interface has come -- it is very responsive, even running from a USB stick!

The major issue I need to resolve to install this on the hard drive is sound.

I use this machine for listening to music.  I use a KingRex T20U ([http://www.6moons.com/audioreviews/kingrex2/u.html](http://www.6moons.com/audioreviews/kingrex2/u.html)), which is an integrated amplifier with built-in USB interface and DAC.

The system appears to detect the device.  When I look in the list of options in "Sound Preferences" I see an options for "Burr-Brown Japan PCM2702 USB Audio (OSS)" and "Burr-Brown Japan PCM2702 USB Audio (ALSA)."

I tried selecting various options in the "Sound Preferences" dialog and clicking the Test button.  Here is what I found:

Option                                    Result
----------------------------------------------------------------------
Autodetect (default)                      No sound

Burr-Brown Japan PCM2702 USB Audio (ALSA) I get the error "audiotestsrc 
                                          wave=sine freq=512 ! 
                                          audioconvert ! audioresample ! 
                                          gconfaudiosink: Could not open 
                                          audio device for playback." 

Burr-Brown Japan PCM2702 USB Audio (OSS)  I hear the test sound!

However, if I choose that option for "Sound Events" and "Music and Movies" I get no sound from Firefox (Flash).

Also, it is my understanding that if I am using OSS, it means that only one application can output sound at a time.  My experience seems to confirm this.  If I play an audio file in RhythmBox, then Pidgin cannot make any sound, for example.

Where should I go from here?  Is there a possibility of using this device with ALSA (Pulse?).  Am I stuck with OSS?  If I am stuck with OSS, is there a way to get sound from Firefox / Flash?

Thanks!

---

### Post by dwinterbourne on 2009-06-08
I have the same problem after upgrading to 9.04. When I originally installed v8 of Ubuntu I had to jump through hoops as well to get sound working with my external sound card in Flash - in that case I disabled all PulseAudio and followed various postings related to getting sound working for Flash. This time around I followed the newer advice against jumping through hoops and went for full imersion in PulseAudio. As long as I don't care to use my external sound card I am quite please with the fact that I didn't need to use any magic flash library, but I really want my external sound card back - it's much higher quality than the internal card.

---

### Post by dwinterbourne on 2009-06-08
I seem to have resolved the issue.

[LIST=1]
[*]asoundconf list - to get the list of your sound cards
[*]asoundconf set-default-card [nameOfYourCard]
[*]Launch PulseAudio Device Chooser (this will place the device chooser in the control tab at the top)
[*]Left click on PA Device Chooser and click on volume control
[*]The first thing I did was set the USB sound card to be the default output device in the Output Devices tab
[*]In the Playback tab click on the drop down arrow on the right hand side of the 'ALSA plug-in [firefox]' (or whatever output stream it displays). Click on 'Move Stream' option and select the USB sound card
[/LIST]
This solved my problem. I seem to be hearing some occassional artifacts in the sound that don't seem right but it's hard to tell what part of the system I can squarely blame that on. I'm listening to PandoraOne and the output goes to set of amplified external speakers.

---

### Post by Charmainek on 2009-08-02
> **dwinterbourne said:**
> I seem to have resolved the issue.

[LIST=1]
[*]asoundconf list - to get the list of your sound cards
[*]asoundconf set-default-card [nameOfYourCard]
[*]Launch PulseAudio Device Chooser (this will place the device chooser in the control tab at the top)
[*]Left click on PA Device Chooser and click on volume control
[*]The first thing I did was set the USB sound card to be the default output device in the Output Devices tab
[*]In the Playback tab click on the drop down arrow on the right hand side of the 'ALSA plug-in [firefox]' (or whatever output stream it displays). Click on 'Move Stream' option and select the USB sound card
[/LIST]
This solved my problem. I seem to be hearing some occassional artifacts in the sound that don't seem right but it's hard to tell what part of the system I can squarely blame that on. I'm listening to PandoraOne and the output goes to set of amplified external speakers.
Thanks, this fixed my problem with pandora/firefox not streaming to my usb speakers.  Pandora/firefox has to be running in order for the options to appear in the drop downs.

---

### Post by LinuxBob on 2009-08-30
"# Launch PulseAudio Device Chooser (this will place the device chooser in the control tab at the top)"


How do you "launch this???

---

### Post by kostkon on 2009-08-30
> **LinuxBob said:**
> "# Launch PulseAudio Device Chooser (this will place the device chooser in the control tab at the top)"


How do you "launch this???
You need to install it first.

---

### Post by LinuxBob on 2009-08-30
OK installed with Synaptics manager

Now:

"# The first thing I did was set the USB sound card to be the default output device in the Output Devices tab"

I do not see the USB speakers in the PulseAudio options, just my ICH5 sound card

# In the Playback tab click on the drop down arrow on the right hand side of the 'ALSA plug-in [firefox]' (or whatever output stream it displays). Click on 'Move Stream' option and select the USB sound card

Again, right clicking on this I do not see a USB speaker option

---

### Post by LinuxBob on 2009-08-31
The instructions worked for one Ubuntu PC, was able to move audio output to my USB speakers.


Still do not see the USB pseakers listed as an audio out option under PulseAudio chooser on the other PC.  


What could be doing this?  I did set ICH5 as defualt audio sometime back.

---

### Post by LinuxBob on 2009-09-01
bump

---

### Post by Nabo00o on 2010-04-11
Hey I am having the same problem with my audio interface UA-25 EX.
I'm using Jaunty, and on preferences > sound, I can only get the test signal from OSS.
ALSA will give the same error as the tread starter reported.

So my problem is that although I can get the test signal from OSS, I can't get any audio out from my low latency external sound card...

I takes midi input though, but that's it.

Julian

Edit: I found that I could hear audio coming from the output by typing this in the terminal:
aplay -D plughw:UA25EX /drive/whatever/song.wav

Still I want the normal programs like totem and rythembox to use it.
In addition the reason to why I bought it was to use it for a DAW, but since no program is cooperating that's hard to accomplish....

---

### Post by tanvir13121987 on 2010-04-11
hi 
i am a new user to linux system and yesterday after installing ubuntu 9.10 on my hp laptop, the sound output is not there.

please help....

my laptop model is hp dv6515tx

CARD - HDA Intel
chip - Realtech ALC268

---

