---
title: "Sound on ThinkPad only works correctly with pulse audio"
date: 2010-08-24
forum: Hardware
---

### Post by oscargodson on 2010-08-24
It was so close to a perfect install ;)

The only thing really missing is this issue with the sound. I've searched all over the forums and i found one thing where you get the model and codecs and write them to a file, however, I can't seem to find what my "model" is because none of the postings have anything about Lenovo laptops. Here is the command they all asked for:
```

cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC269
Codec: Intel G45 DEVIBX

```

With that info, how do I get the model, and how do I get my speakers to stop playing when headphones are plugged in. Also, I don't have any software installed like pulse audio either, so it's not that.

Thanks so much to whoever can answer this... :)

I've been trying to get someone to just respond forever... and nothing...

---

### Post by rCXer on 2010-08-25
What type of thinkpad do you have? (I don't know the answer to your question but this may help others find the answer)

---

### Post by lidex on 2010-08-25
> **oscargodson said:**
> It was so close to a perfect install ;)

The only thing really missing is this issue with the sound. I've searched all over the forums and i found one thing where you get the model and codecs and write them to a file, however, I can't seem to find what my "model" is because none of the postings have anything about Lenovo laptops. Here is the command they all asked for:
```

cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC269
Codec: Intel G45 DEVIBX

```

With that info, how do I get the model, and how do I get my speakers to stop playing when headphones are plugged in. Also, I don't have any software installed like pulse audio either, so it's not that.

Thanks so much to whoever can answer this... :)

I've been trying to get someone to just respond forever... and nothing...
It would help if you used a more aptly descriptive thread title. If you have a default ubuntu install, you have pulseaudio. If your "Sound on ThinkPad only works correctly with pulse audio", then it's working correctly.

As for your "model":
```
ALC269
======
  basic		Basic preset
  quanta	Quanta FL1
  eeepc-p703	ASUS Eeepc P703 P900A
  eeepc-p901	ASUS Eeepc P901 S101
  fujitsu	FSC Amilo
  lifebook	Fujitsu Lifebook S6420
  auto		auto-config reading BIOS (default)

```
I would try basic and auto (separately) . Here's how:
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=basic 
```
Save. Close. Reboot. 
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.
[U]
Change basic to auto if that doesn't work.[/U]

---

### Post by oscargodson on 2010-09-27
> **rCXer said:**
> What type of thinkpad do you have? (I don't know the answer to your question but this may help others find the answer)

I have a L512

---

### Post by oscargodson on 2010-09-28
> **lidex said:**
> It would help if you used a more aptly descriptive thread title. If you have a default ubuntu install, you have pulseaudio. If your "Sound on ThinkPad only works correctly with pulse audio", then it's working correctly.

As for your "model":
```
ALC269
======
  basic		Basic preset
  quanta	Quanta FL1
  eeepc-p703	ASUS Eeepc P703 P900A
  eeepc-p901	ASUS Eeepc P901 S101
  fujitsu	FSC Amilo
  lifebook	Fujitsu Lifebook S6420
  auto		auto-config reading BIOS (default)

```
I would try basic and auto (separately) . Here's how:
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=basic 
```
Save. Close. Reboot. 
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.
[U]
Change basic to auto if that doesn't work.[/U]

The basic didn't do anything but make the mic not work unfortunately.

Auto put it back to where it's supposed to be. I can change the mic/speaker volume up/down with alsamixer in terminal but it still doesn't recognize when headphones are plugged in/out.

Also, about the title, I had a default install of Ubuntu 10.04 and Pulse Audio was not installed. Without it, i didn't have the options to change between headphones, output, and speakers. And if i uninstall pulse audio right now, which I installed through the software center ill be unable to change it from the current setting.

---

