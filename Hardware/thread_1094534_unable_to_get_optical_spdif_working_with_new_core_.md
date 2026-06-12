---
title: "unable to get optical spdif working with new core i7 system"
date: 2009-03-12
forum: Hardware
---

### Post by heper on 2009-03-12
I currently have the intel x58 smackover motherboard and installed
jaunty on it.

it comes with the ICH10 ALC889 codec.
 

This offcourse gets automatically detected on bootup.I get some
sound out of the analog outputs and no sound at all out of the optical spdif
(normally it should light up when ya look at the cable but it does not!!)

What have i tried:

i've turned on the IEC958 stuff in alsamixer
i've manually (with script found on this forum) upgraded alsa to 1.0.19
i've tried a zillion model options in /etc/modprobe.d/alsa-base.conf

here you'll find some output from various logs and confs and hope
that someone will be able to figure this out for poor me ;)
```

heper@heper-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889 Digital [ALC889 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
heper@heper-desktop:~$ 

```
```
heper@heper-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889 Digital [ALC889 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
heper@heper-desktop:~$ aplay -L
default:CARD=Intel
    HDA Intel, ALC889 Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, ALC889 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC889 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC889 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC889 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC889 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC889 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC889 Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)

```
```
[heper@heper-desktop:~$ less /proc/asound/card0/
codec#2    oss_mixer  pcm0p/     pcm1p/     
id         pcm0c/     pcm1c/     pcm2c/     
heper@heper-desktop:~$ less /proc/asound/card0/codec#2 








































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































































Codec: Realtek ALC889
Address: 2
Vendor Id: 0x10ec0889
Subsystem Id: 0x80860022
Revision Id: 0x100004
No Modem Function Group found
.
.
.



```

So AFAIK it should work. It detects the digital output, it doesn't 
give any error whatsoever but for some reason it won't work.


Any clues ?

thanks

---

### Post by heper on 2009-03-13
anyone ?

---

### Post by heper on 2009-03-13
For those of you who have a clue, bellow you can find
a link to the output of alsa-info.sh

[http://pastebin.com/m16c96953](http://pastebin.com/m16c96953)


thanks

---

### Post by Plexor on 2009-09-24
Did you ever have any luck with this?

---

### Post by t0mm1e on 2009-11-05
Same problem here with ALC889 onboard DP55KG motherboard.

Everything seems to work, except volume in alsamixer is always 00 and I can't change it. 

amixer output of alsainfo show the digital output has no volume capabilities?

Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined cswitch cswitch-joined
  Playback channels: Mono
  Capture channels: Mono
  Mono: Playback [on] Capture [on]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]

The other analog jack outputs have pvolume capability.

---

### Post by xubuntu84 on 2010-12-25
> **t0mm1e said:**
> Same problem here with ALC889 onboard DP55KG motherboard.

Everything seems to work, except volume in alsamixer is always 00 and I can't change it. 

amixer output of alsainfo show the digital output has no volume capabilities?

Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined cswitch cswitch-joined
  Playback channels: Mono
  Capture channels: Mono
  Mono: Playback [on] Capture [on]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]

The other analog jack outputs have pvolume capability.
Any luck on getting your sound to output over optical on the DP55KG? I'm having no luck getting ANY sound out.

I'm not too familiar with getting sound working in Linux, so I might have not done everything yet.  So far, I have installed Gnome Alsa Mixer, and have set all my sound levels to mid-range, but nothing happens when I test the speakers using Sound Preferences.

Intel's DP55KG page shows that sound support is native in Linux.

---

### Post by t0mm1e on 2010-12-27
Nope, I've never had success on that motherboard.

I've upgraded recently to a new system with DX58SO motherboard, and now spdif is working fine.
Soundsystem still has some quircks, I cannot control analog an digital separately for example, and the headphone jacks have quite a lot of noise on the front.

But altogether I'm quite happy with this new motherboard.

No solution for the problems with the other motherboard though!

---

### Post by lidex on 2010-12-29
@benmctee
What profile do you have selected in 'Sound Preferences'?
This look familiar:
[http://alsa.opensrc.org/DigitalOut](http://alsa.opensrc.org/DigitalOut)

With a digital profile selected, play an audio file and check pavucontrol.
Are you getting meter deflection?

---

### Post by reibax on 2011-02-19
OK, I might be able to help here. I know it's long since the question was brought to light, but I haven't faced this problem myself until now.

Everything I'm explaining here worked for my system running Ubuntu 10.10 Maverick Meerkat.

This is how I got my optical SPDIF output to work on an ALC889 equipped ACER Aspire 5935G: 

At first, I could have audio through the analog output, and also from the HDMI digital output (which in my case is hosted in the same 3.5mm connector used for headphones), but there was no way I could get the audio going through my Optical S-PDIF output.

After trying many different suggestions from many different sources, I decided to go back to Ubuntu's default sound configuration based on pulseaudio and alsa installed direclty from official Ubuntu repositories, got every configuration file modified in /etc back to standard, and removed every configuration file in my profile:

```

rm ~/.pulse*
rm ~/.alsa*

```

Reboot the system in order to get those re-generated. Once on my desktop everything was back to where I was with a freshly installed Ubuntu sound-wise.

The problem seems to be related to ALSA selecting the wrong hardware setup related to the soundcard. In my case, doing the following:

```

**laptop:~$** lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)


**laptop:~$** aplay -l
**** Lista de PLAYBACK dispositivos hardware ****
tarjeta 0: Intel [HDA Intel], dispositivo 0: ALC889 Analog [ALC889 Analog]
  Subdispositivos: 0/1
  Subdispositivo #0: subdevice #0
tarjeta 0: Intel [HDA Intel], dispositivo 1: ALC889 Digital [ALC889 Digital]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0

```

Shows me that my soundcard is a Realtek ALC889 chipset-based one, which matches what the documentation about my laptop says.

The key to this matter is that even though ALSA knows what my chipset is, every hardware maker can connect the same chipset in different ways, and that affect audio output behaviour, so I decided to look for the specific models supported by ALSA:

```

zless /usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz

```

Inside that file, I went to the **ALC882/883/885/888/889** section, and looked for models similar to my laptop, in my case:

```

  acer          Acer laptops (Travelmate 3012WTMi, Aspire 5600, etc)
  acer-aspire   Acer Aspire 9810
  acer-aspire-4930g Acer Aspire 4930G
  acer-aspire-6530g Acer Aspire 6530G
  acer-aspire-7730g Acer Aspire 7730G
  acer-aspire-8930g Acer Aspire 8930G

```

So I started trying out each of the models. The way to do that is edit /etc/modprobe.d/alsa-base.conf :

```

sudo gedit /etc/modprobe.d/alsa-base.conf

```

And, if there is no line containing options for your soundcard module (snd-hda-intel in my case), add the following line:

```

options snd-hda-intel **model=acer-aspire-8930g**

```

To test a model, I would edit the name after the model tag, and reset my computer in order to get the new configuration running.

I guess there might be faster ways to do it like reloading the module, or restarting pulse audio, but I didn't know for sure if that would work, and I wanted to take no chances.

To test the behaviour of each model, went to System->Preferences->Sound, and in the hardware tab I would test each profile by setting it, and after doing it starting to play a sound file with Totem.

This way you will be likely to find a model that behaves the same your motherboard/laptop is thought to behave.

In my particular case, it was acer-aspire-8930g, and with the Analog Stereo Duplex I had audio running through my Optical S/PDIF when having my cable connected. ¡Perfect!

Just one more thing... since Pulseaudio doesn't seem to support audio passthru, you can use gstreamer-properties to get gstreamer based software to make use of ALSA whithout going through pulseaudio. VLC can also be configured to do passthru using ALSA in the audio preferences tab.

I hope this helps!

---

### Post by scokar on 2011-03-13
> **reibax said:**
> OK, I might be able to help here. I know it's long since the question was brought to light, but I haven't faced this problem myself until now. [...]
I hope this helps!

Hello!  Thank you very much, this helped solve my problem. I was going nuts after the ubuntu live CD worked but my installs never did.

Your solution worked for me.  thank you!

[B]Motherboard:  Gigabyte GA-H57M-USB3

Audio codec:   Realtek ALC889a

model:  intel-alc889a  
[/B]

model information from via zless /usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz and searching for ALC889


```
cp /etc/modprobe.d/alsa-base.conf /etc/modprobe.d/alsa-base.conf.orig
vi /etc/modprobe.d/alsa-base.conf 

```
go to bottom of file

add:
   
```
option snd_hda_intel  model=intel-alc889a
```

reboot

then in terminal run alsamixer to be sure the spdif ( IEC958 ) channels are **NOT** muted (00 for active vs MM for muted) and set the  "<channel>"  to 2 or 6 or 8  and ESC to exit

inside

System->Preferences->Sound's hardware tab, I had to select "Analog Stereo Duplex"

To finally get any sound.

I was able to test multichannel sound by playing a dolby digital sound file I have  ("this is the left channel... " etc)

via:  aplay -D hw:0,1  surround.wav

---

### Post by scokar on 2011-03-15
> **scokar said:**
> ... To finally get any sound.

I was able to test multichannel sound by playing a dolby digital sound file I have  ("this is the left channel... " etc)

via:  aplay -D hw:0,1  surround.wav

spoke too soon.   stereo only, no 5.1.

---

### Post by lidex on 2011-03-17
@scokar
Your chipset is Intel H57 Express not Ibexpeak so I am not convinced you selected the correct model. Also selecting analog-duplex will only allow stereo. Your board supports 8-channels, is that what you selected in alsamixer? Try *6stack-dig* as your model.

---

### Post by scokar on 2011-03-18
Hello lidex

I am able to get stereo and 5.1 sound now, the problem was a setting in gstreamer & on my receiver  - I had to explicitly tell it the stream coming in is DTS or DD when playing movies xbmc.


Motherboard: Gigabyte GA-H57M-USB3
Audio codec: Realtek ALC889a
model: intel-alc889a 


1.  /etc/modprobe.d/alsa-base.conf:
add ->  options snd-hda-intel model=intel-alc889a

2.  sound preferences -> hardware -> Analog Stereo Duplex
		
3.  terminal -> "gstreamer-properties"
*) Audio tab -> select ALSA - Advanced Linux Sound Architecture, for Default Output. 
*) Device ->  choose the digital device,  e.g  ALC889A digital

4. XBMC:
*) Settings -> Audio-> Audio Output -> Optical/Coax
    			Speaker Configuration 5.0  (because I have no subwoofer yet)
			Dolby Digital AC3 Capable Receiver  
			DTS Capable Receiver
			Audio Output -> Default
			Passthrough Output Device -> IEC958

5. Onkyo receiver: 
*) set proper AV input (i.e. video1, etc)
*) set AV input's audio (i.e. optical, coax)
*)  set "DSP" -> DTS  (or DD?) based on movie being played if necessary

Hope this helps

---

### Post by kingfishr on 2011-04-23
reibax, scokar: you guys are my new favorite people. I was so frustrated with this, but your suggestions did the trick.

---

### Post by reibax on 2011-04-23
I'm really glad we could help. It feels really good being able to be on the helping side for once! :D

---

