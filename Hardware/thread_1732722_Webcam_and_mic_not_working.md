---
title: "Webcam and mic not working"
date: 2011-04-18
forum: Hardware
---

### Post by Ozma on 2011-04-18
Hello everyone,

I'm a bit new to Ubuntu and obviously new to the community too, so I hope you guys can help me out a bit. I ended up installing Ubuntu 10.10 on my laptop hoping that the webcam would work (as Toshiba's webcam drivers do not work on Windows 7). A friend of mine who knows a lot about Linux has been trying to help me out here, but he has found no solution, so here it goes:

How can I make my webcam and mic work?

I have a Toshiba Satellite A300, running on Ubuntu 10.10. When I open Cheese, the program just crashes. I tried with Fedora too and even Jolicloud, and the same problem occurs. I also have no idea why the mic would not work. I tried the sound recorder, and it was no use. When I use the command lsusb I get this output:

```
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0bda:8197 Realtek Semiconductor Corp. RTL8187B Wireless Adapter
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

I really hope you guys can help me out here because this whole webcam issue is gonna kill me at this rate!! 

Thanks in advance :)

---

### Post by Ozma on 2011-04-20
I really need help here, guys. Seriously nobody knows how to fix this?

---

### Post by lidex on 2011-04-21
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by UncleBoxy on 2011-09-05
I have a similar question to the original poster.  My webcam is working fine for video, but it isn't picking up any audio.  I downloaded the alsa-info bash script and ran it.  The output is at [http://www.alsa-project.org/db/?f=851636ec80a3bc0461673ffa390853957bcd58d6](http://www.alsa-project.org/db/?f=851636ec80a3bc0461673ffa390853957bcd58d6)

---

### Post by lidex on 2011-09-18
> **UncleBoxy said:**
> I have a similar question to the original poster.  My webcam is working fine for video, but it isn't picking up any audio.  I downloaded the alsa-info bash script and ran it.  The output is at [http://www.alsa-project.org/db/?f=851636ec80a3bc0461673ffa390853957bcd58d6](http://www.alsa-project.org/db/?f=851636ec80a3bc0461673ffa390853957bcd58d6)

First, for mic problem, check this.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

Then go to 'Sound Preferences' to select the correct device and mic ('Connector' option) and unmute your mic in 'Input' tab.
Make sure you have selected a profile with 'duplex' or 'analog input' for the correct sound device on the 'Hardware' tab.
Use Pulse Audio Volume Control (pavucontrol) to unlock stereo sliders for the mic in 'Input Devices' tab. Drag the right slider down to zero. 

From alsa documentation:
> Capture Problems
~~~~~~~~~~~~~~~~
The capture problems are often because of missing setups of mixers.
Thus, before submitting a bug report, make sure that you set up the
mixer correctly.  For example, both "Capture Volume" and "Capture
Switch" have to be set properly in addition to the right "Capture
Source" or "Input Source" selection.  Some devices have "Mic Boost"
volume or switch.

When the PCM device is opened via "default" PCM (without pulse-audio
plugin), you'll likely have "Digital Capture Volume" control as well.
This is provided for the extra gain/attenuation of the signal in
software, especially for the inputs without the hardware volume
control such as digital microphones.  Unless really needed, this
should be set to exactly 50%, corresponding to 0dB -- neither extra
gain nor attenuation.  When you use "hw" PCM, i.e., a raw access PCM,
this control will have no influence, though.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

From ubuntu wiki:
> Changing default subdevice configuration

Some sound devices have multiple capture subdevices (eg. hda-intel), 
but pulseaudio only seems to detect the parent device, and only listens to subdevice #0. 
ALSA may not be configured to use your preferred device as subdevice #0 by default.

Open the pulseaudio record meter (pavumeter --record)
Talk into your chosen device while you carry out the process and watch the meter.
Some channels are quite noisy even with no input (especially on integrated chipsets), 
so we are watching for movements that correspond to our voice. 

Use alsamixer -c n (where n is your sound card number, probably 0)
Press F4 to get to the capture console
Make sure the first capture channel is enabled ("CAPTUR" in red, press space to toggle), 
and the volume turned up.
Check the first input source is switched to your chosen plug (Mic, in my case) 
At this point, you should see the record meter bouncing in response to your voice.
I found that I had to repeat this procedure each time I wanted to use the Mic, 
even though the settings "stuck" in the mixer, something in the soundcard wasn't initialized 
until it was repeated. This also works if you use the "Options" tab in the standard mixer app to do the same thing.

---

