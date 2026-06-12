---
title: "microphone with dell m1330"
date: 2009-01-07
forum: Hardware
---

### Post by Adnanius on 2009-01-07
neither internal or external microphones are working. 
I tried changing devices in the Sound Preferences, checked capture level is at max in alsamixer, still I can't record anything using Sound Recorder or in Skype. 

[[IMG]http://img339.imageshack.us/img339/9741/soundpreferencesxv7.th.png[/IMG]](http://img339.imageshack.us/my.php?image=soundpreferencesxv7.png) 

here's output of lspci regarding HDA intel: 

>  Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)
	Subsystem: Dell Device [1028:0209]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 21
	Region 0: Memory at f6ffc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel


I would be very thankfull for any help

---

### Post by Adnanius on 2009-01-10
Anyone??

---

### Post by khelben1979 on 2009-01-10
There is a button in one of those sound mixer programs where you can untick the mute button. Try that.

I know that kmix has one for instance.

(I'm not sure if this will do the trick, but it could be worth a try)

---

### Post by Adnanius on 2009-01-10
In the volume control, when I untick the mute, close the volume control, and reopen it, it's mute again!(the red cross is back)!

---

### Post by khelben1979 on 2009-01-10
What do you see when you look at the lamps in the KMix application under the switches tab?

You could try experimenting here, I think.

---

### Post by linux_tech on 2009-01-10
what version of ubuntu do you have? 32bit or 64 bit?

If you have 32 bit for external mic, you may try this:
 ```
wget http://people.ubuntu.com/~rtg/linux-backports-modules-2.6.22-14-generic_2.6.22-14.11UNRELEASED_i386.deb

sudo dpkg -i linux-backports-modules-2.6.22-14-generic_2.6.22-14.11UNRELEASED_i386.deb

sudo reboot
```
ref:
[http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Built_In_Digital_Mic_Does_Not_Work](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Built_In_Digital_Mic_Does_Not_Work)

For 64bit more info here:
[http://ubuntuforums.org/showthread.php?t=702642](http://ubuntuforums.org/showthread.php?t=702642)

---

### Post by Adnanius on 2009-01-10
You're right, I should have specified what ubuntu version I'm using. 
I installed intrepid 8.10, 64bit, and all the solution talking about the 'Digital Input Source' only work with 8.04, right? Actually I didn't find ANY thread or forum giving a solution for 8.10!
I don't have Kmix for instance, and don't think that installing kmix would change anything, don't you think so?
This is what my volume control 'recording' display:
[IMG]http://img384.imageshack.us/img384/3039/screenshotvolumecontrolva3.png[/IMG]

When I unmute the microphones, close the volume control, and rreopen it, I find the 2 microphones muted again, by themselves.
Still, no internal or external mic is working.

---

### Post by linux_tech on 2009-01-10
Under System -> Preferences -> Sound
try both alsa and autodetect options.

Try temporarily disabling pulseaudio 
```
killall pulseaudio
```


Install esound
```
sudo apt-get install esound
```

Install gnome alsamixer
```
sudo apt-get install gnome-alsamixer

``` 
To open gnome-alsamixer type
```
gnome-alsamixer

```

check all settings, make sure nothing is muted

See if any of these makes a difference

---

### Post by Adnanius on 2009-01-10
Tried as you said, didn't work. 
I noticed that in GNOME ALSA Mixer, I check the "Rec." boxes under the 3 'capture' (2 integrated mics and the external one). As soon as I OPEN Sound Recorder, the boxes uncheck automatically.
Tried the different options in Sound Preferences, didnt work. 
looks like I have alsa and oss installed. may this be the problem?

---

### Post by GJLenon on 2009-01-11
Hello,

I had the same issue.

Here's what I did.

Go to:  System > Preferences > Sound

Under Audio Conferencing look for "Sound Capture"

Set it to the USB Audio (it should be "<sound card> USB Audio (ALSA)").

Or something to that effect... I'm rather new to ubuntu, sorry.

Anyway, that worked for me, hope it helps!

---

### Post by Adnanius on 2009-01-11
thank you GJLenon, but it seems you have a usb audio device, and that's not my case.

---

### Post by GJLenon on 2009-01-11
I'm sorry, I assumed when you said you had an external microphone that you had a USB one.

Under Sound Capture, have you tried using the various options and seeing if one of those work?

---

### Post by jawahar on 2009-02-07
Adnanius, 

Next to playback, recording, and switches, you need an options tab. 
1. Click on "preferences" and check the "Digital Input Source" box.
2. In the options tab, try selecting "Analog Inputs" for external mic, and "Digital Mic 1" for the internal mic

---

### Post by Adnanius on 2009-02-07
I don't have a "Digital Input Source" box, I have 2 options:
[LIST=1]
[*]Capture:Monitor Source of ALSA PCM on front:0 (STAC92xx Analog) via DMA (PulseAsudio Mixer)
[*]Capture: ALSA PCM on front:0 (STAC92xx Analog) via DMA (PulseAsudio Mixer)
[/LIST]
And on both, I only have the "Master" option.

---

