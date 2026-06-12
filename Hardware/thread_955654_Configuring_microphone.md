---
title: "Configuring microphone"
date: 2008-10-22
forum: Hardware
---

### Post by DarkLordPonder on 2008-10-22
Hey, everyone :)

I'm a somewhat new Ubuntu user, previously from Windows. I've got a laptop, and the microphone is mounted above the screen.

I can't seem to get my microphone to work at all. I found something in support that told me to go to Volume Control->Edit->Preferences->checkmark 'Capture', close Preferences, click on recording, click on mic and bullhorn to unmute, drag sliders to max

At first, this did absolutely nothing. When I checked some other things, I went into Sound Recorder, and after I recorded and hit playback, all I got was a really fast clicking sound, kind of like a chainsaw.

Here are the things that I have checkmarked:
Master
Headphone
PCM
Front
Front Mic Boost
Mic Boost
Capture

When I open volume control and click on the 'Recording' tab, I have two things there, Capture and Capture 1. All sliders in volume control are set to maximum volume.

So, how do I make my microphone work, then?
Thanks,
DLP

---

### Post by teaker1s on 2008-10-22
if your sound hardware is hda-intel look [here]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

most likely your model setting is incorrect

---

### Post by DarkLordPonder on 2008-10-23
> **teaker1s said:**
> if your sound hardware is hda-intel look [here]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

most likely your model setting is incorrect

I don't have a mac, though. I've got an Acer. Will that work for me?

---

### Post by teaker1s on 2008-10-24
yes alsa model line try either:-auto,basic or acer the guide explains how.

---

### Post by DarkLordPonder on 2008-10-24
sorry if I'm a total n00b at this :(

I'm either not understanding the stuff on the page or it's just not working.

I tried this line:
> sudo gedit /etc/rc.local
When I did that, it asked for a password, but wouldn't let me type anything in response. 

I'm fairly certain that I have all the stuff I need installed. Even so, I tried it, but it again asked me for a password that it again wouldn't let me enter, assuming I knew it which I'm not sure that I do.

I tried this one next:
> cat /proc/asound/card0/codec#* | grep Codec

That seemed to work. It told me that I had a RealTekALC268 soundcard. So, I entered the next line of command:
> /usr/src/KERNEL_VERSION/Documentation/sound/alsa/ALSA-Configuration.txt
The terminal responded "No such file or directory"
It gave me a link to try if that happened, but looking at it I had no idea what they were talking about.

So, I'm still stuck :( The manual has nothing about the microphone for any operating system.

---

### Post by teaker1s on 2008-10-24
think the codec line is misleading, I have hda intel and the command will bring up realtek codec.
Lets list your pci devices in a nice sectioned manner.
```
sudo lspci -v
```
now it's going to ask for a password because we are using "sudo" to become sudo root. enter your normal password-note cursor will not move but it will register your password.

now my sound is
[B]00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
[/B]
quick google tells me
    * 0000:00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2) 

        * Driver: snd-hda-intel 

if you get stuck then paste the output and I'll help you:popcorn:

---

### Post by DarkLordPonder on 2008-10-25
> 00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Acer Incorporated [ALI] Realtek ALC268 audio codec
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at fc300000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Unknown type IRQ 0

I googled the first line, but I didn't find anything that helped me. The closest I got was [this page,](https://help.ubuntu.com/community/SoundTroubleshooting?action=show&redirect=DebuggingSoundProblems) but it still didn't actually work.

> sudo nano /etc/modprobe.d/alsa-base Then add this options line options <snd module name here i.e. snd-via82xx> mpu_port=0x330 OR if you already have a options line for this soundcard add mpu_port=0x330 to the line. 

I entered those lines (not the last, though, because that line wasn't in the rest of my information) but it just waited for me to add more information.

So, what should I do now?

---

### Post by teaker1s on 2008-10-25
hda-intel I believe

Terminal
```
sudo gedit /etc/modprobe.d/alsa-base
```

Then paste the following line at the end of the file (change MODEL with the type of sound card's [COLOR="Sienna"]model[/COLOR]: try basic or auto or acer

```
options snd-hda-intel model=[COLOR="Sienna"]MODEL[/COLOR]
```

save and reboot

---

### Post by DarkLordPonder on 2008-10-25
arg.... chainsaw sound again :( I wonder what's wrong with this thing?

---

