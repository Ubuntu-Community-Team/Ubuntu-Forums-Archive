---
title: "HDMI Audio, Dell M1330 GeForce 8400M GS, Ubuntu 10.10 64bit"
date: 2011-12-04
forum: Hardware
---

### Post by folken1983 on 2011-12-04
Dear ubuntuforums,

I know this is an old topic, yet I've been struggling with this for a long time now, without finding a solution.

Problem is simple, HDMI video just fine, audio seems to be set up fine, but just does not reach the tv.

After reading quite a lot, it seems that some people with my same laptop got HDMI audio working almost out of the box, so I'm convinced there must be a solution out there.


This is as far as I got:

Important info:

Dell XPS m1330
Ubuntu 10.10 64bit
Geforce 8400m GS (NVIDIA Driver Version: 290.10)

Hardware devices (aplay -l):

card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

the above means, in principle, that one can send audio to hw:0,0 (laptop) or hw:0,1 (the digital output, supposedly the tv/hdmi out).

More precisely:
cat /proc/asound/card0/codec#* | grep Codec
Codec: SigmaTel STAC9228

Module in:
/etc/modprobe.d/alsa-base.conf
added:
options snd_hda_intel model=dell-bios

In pulseaudio volume control I can switch to "Digital Stereo (IEC958) Output", but no sound comes from tv.

In alsamixer S/PDIF is on, S/PDIF_D is on, S/PDIF_P is on Digital
(I also played with muting/unmuting without success)

Some tests with mplayer:
mplayer test.wav -ao alsa:device=hw=0.0
this sends output to laptop and works fine

mplayer test.wav -ao alsa:device=hw=0.1
this should send output to hdmi out, but no sound is heard from tv or laptop. No error is give so it seems that audio is produced correctly. I assume this is equivalent to selecting "Digital Stereo (IEC958) Output" in pulseaudio.

I read in a few forums that the digital output comes from the SigmaTel STAC9228 chip and is sent to the nvidia card, which then just passes it to the actual hdmi cable. So, this might be a problem of nvidia drivers, but even the latest 290.10 nvidia drivers don't make a difference.

Any help is appreciated, thanks in advance.

---

### Post by JamieKitson on 2011-12-05
Hi Folken,

as I said in [my other post](http://ubuntuforums.org/showthread.php?t=1144410), rather embarrassingly all I needed to do was to unmute and/or switch on, the digital out, which apparently was labelled "IEC958" in alsamixer.

Unfortunately I haven't had an M1330 for a couple of years now so I can't really help you any further than that.

Could you post a screen shot of your alsamixer?

Cheers, Jamie

ps, have a look here: [http://alsa.opensrc.org/DigitalOut#Check_your_mixer](http://alsa.opensrc.org/DigitalOut#Check_your_mixer)

---

### Post by folken1983 on 2011-12-05
Hi JamieKitson, thanks for your reply,

I wish the solution were just an embarrassing one. In my alsamixer I have S/PDIF in place of IEC958, but this could be just because I have a more recent version of alsa/nvidia drivers with respect to the one you had back then. I did try to play with alsamixer, but with no luck.

It is a pity you do not have your m1330 with latest updates, I was hoping you could check your configuration and see the differences.

I also read the ALSA wiki, which was really helpful, but not enough... that's why I'm posting to the forum :)

Screen attached.

---

### Post by gordintoronto on 2011-12-05
What happens when you press F6 to select the sound card?

By the way, on my laptop, I just used "Sound Preferences" to select the sound device. Now that I'm running 11.10, "everything has changed."

---

### Post by folken1983 on 2011-12-06
Hi gordintoronto,
I have only one card to select. This should be ok, as pointed out by JamieKitson in his post [here]("http://ubuntuforums.org/showthread.php?t=1144410") two years ago. My aplay -l output is exactly as his was:

> 
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by gordintoronto on 2011-12-06
In the post you referred to, he said, "I played around in alsamixer until I got sound from the TV, unmuting IEC958 and setting IEC958 Playback Source to Digital."

Have you done that?

---

### Post by folken1983 on 2011-12-06
Yes I have played with alsamixer, as I explained in the posts above. The only difference is that I do not have IEC958 but S/PDIF, which I assume is ok.

---

### Post by gordintoronto on 2011-12-06
S/PDIF is an optical connector. You attach a fiber-optic cable from it to a sound processor (fancy name for an amp) which has S/PDIF input.

It's unlikely that S/PDIF is relevant to your problem or its solution.

Could you post a screen shot from running Sound Preferences and clicking the Output (and maybe Hardware) tab?

---

### Post by JamieKitson on 2011-12-07
Sorry I can't be of more help, I seem to remember my IEC958 being where your S/PDIF, or possibly toggling to IEC958.

Other things:

* Presumably Gnome has a mixer and audio device manager, could this help, or be hindering?

* Are you sure your TV accepts audio over HDMI? I seem to remember having some device that didn't. What model is it? Could it be "listening" on another channel?

* Could you check whether it works on Windows?

---

### Post by folken1983 on 2011-12-08
@gordintoronto

I'm not sure about the S/PDIF, I read on the alsa wiki that this might indicate digital audio and is sometimes found in place of IEC958 (see [here]("http://alsa.opensrc.org/DigitalOut#Find_your_device")), in particular I quote from there

> If your card does not show an IEC958 device, look for S/PDIF or digital.

Yet, it is strange that I find S/PDIF where JamieKitson reported to have IEC958 on the same laptop.

See attached screenshots of sound settings, where I show:
1. Hardware tab, analog output set
2. Hardware tab, digital output set
3. Output tab when digital output is set in Hardware

@JamieKitson

1. Yes, I tried using a Gnome alsamixer, it shows IEC958 in place of S/PDIF (which was shown in terminal alsamixer). Plus it has a couple of extra tick boxes that don't actually work. In fact there is an additional "IEC958 Playback source" tickbox, but when I set it doesn't do anything and does not stay checked when I close and reopen gnome alsamixer. I think it is just a bug of gnome alsamixer.

2. My TV is a samsung t27a300, very new, just out in the market. It has two hdmi inputs, but sound does not work for any of them with my laptop. I wouldn't see why it should be the tv.

3. I have a dual boot with Win XP. Hdmi audio does not work in XP either. And it looks like a similar situation. I tried even older versions of nvidia drivers as someone suggested [here]("http://forum.notebookreview.com/dell-xps-studio-xps/414445-m1330-hdmi-audio-nvidia-graphics-xp.html"), but the result is the same. In sound settings -> advanced, I have a S/PDIF tickbox which should enable/disable hdmi output, but it doesn't work.

At this point, it might well be either the TV not accepting the audio format (too old?) or the laptop having broken hardware. As a side note, my motherboard (and so everything from nvidia card to sigmatel audio) was replaced a couple of years ago. Maybe the replacement hardware was defective or somehow different?

---

### Post by gordintoronto on 2011-12-08
On my desktop computer, the video card has HDMI out, but does not produce sound. It came with a cable to take sound output from the motherboard, and put it on the HDMI output.

Perhaps there is something along those lines in your computer, which was not connected when they replaced the motherboard. It seems quite likely, if XP and Ubuntu both have the problem.

---

### Post by folken1983 on 2011-12-09
I thought about this possibility as well. Yet is seems quite unlikely, as nvidia chip and sigmatel chip are both integrated on the motherboard and probably communicate via bus. Yet I can't be sure. (Well one way to know, would be to be able to read this diagram [here]("http://www.getteck.com/LinkClick.aspx?fileticket=QaTRol1akBU%3d&tabid=94"))

Next thing I'm going to try is to test a different tv, probably this week end.

---

### Post by folken1983 on 2011-12-11
I tested the laptop with a slightly older tv with hdmi, using both ubuntu and windows xp. Once again, no sound via hdmi. I'm back to think what could be wrong in the laptop. The only thing that seems possible to me at this point is failed communication between nvidia and sigmatel.

---

