---
title: "Hardy Heron - Microphone problem!"
date: 2008-05-11
forum: Hardware
---

### Post by monkeys on 2008-05-11
**Gateway Model MA7**
HDA Intel, SigmaTel STAC9250

I can't seem to get my microphone to work! I've tried solutions found here: [http://ubuntuforums.org/showthread.php?t=314383](http://ubuntuforums.org/showthread.php?t=314383) and still, no resolve. I've also made sure the Front Mic is selected on Alsamixer and nothing there is muted.

**Edit:** Sound works just fine.

When I test the Sound Capture (ALSA selected) in Sound Preferences, I get > "Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat'".

Both Skype and Sound Recorder show the mic doesn't work. Please help!

---

### Post by tgalati4 on 2008-05-11
I assume you tried the following for a stac9200 chipset:

-----------------

Try this:

1. backup your existing /etc/modprobe.d/alsa-base
2. append the following to the end of the file:

options snd-hda-intel model=ref

Reboot, tweak your levels in alsamixer to your liking, record, playback.

---

### Post by monkeys on 2008-05-11
I've tried that -- nothing. Sound Recorder just freezes, Skype plays back nothing.

---

### Post by monkeys on 2008-05-21
Bump. Still no luck.

---

### Post by MockY on 2008-10-04
I have the same chipset as you and this has been an issue since I first bought my laptop. I have tried all versions of Ubuntu on it, starting with Edgy, and I have been excited every time a new release is available, just to see if the mic would work this time. I just tried out the Intrepid beta and this issue is still present. It's really amazing that this is still an issue since this is an old chipset and should be supported by now.

---

### Post by skubler on 2008-11-11
I have exactly the same problem with Intrepid.

My microphone is in a Phillips SPC520NC USB webcam,

lsusb:-

Bus 002 Device 002: ID 0471:0334 Philips

Intrepid recognizes the card as per

cat /proc/asound/cards

 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xefff4000 irq 22
 1 [Camera         ]: USB-Audio - USB Video Camera
                      USB Video Camera at usb-0000:00:0b.1-1, high speed

However, I can not capture any sound via this microphone using either skype or sound recorder.

If I plug a microphone into the front or back inputs on my computer I can not capture any sound from those either.

I do not have this problem when running Vista on the same hardware.

All other sound works fine on my machine under Intrepid.

I have been through the whole gamut of suggested fixes provided by these forums or other websites but nothing works. 

My closest point has been getting the mic recognized by pulsaudio and being used when I make a test call in skype. However, even though pulseaudio manager shows the correct device being in use, no audio is being captured. 

All of this is highly frustrating.

---

### Post by treesurf on 2008-11-11
I have been struggling with this same issue since Edgy.  I finally got a little bit of satisfaction by installing one of the latest versions of ALSA which has some support.  Microphone sound quality isn't great, but it is there finally.  This thread is the one that finally brought my mic to life:

[http://ubuntuforums.org/showthread.php?t=820959&highlight=power+management](http://ubuntuforums.org/showthread.php?t=820959&highlight=power+management)


Edit:  I also have the STAC9250 sound card.

---

### Post by treesurf on 2008-11-11
sorry, double post

---

