---
title: "Thinkpad microphone problem"
date: 2010-09-18
forum: Hardware
---

### Post by amgmagician on 2010-09-18
Hi,

[INDENT]I have a T61 Thinkpad with Ubuntu 10.04. My internal mic didn't work however the external mic worked well. It seemed the input volume is low. In order to fix the internal mic problem I tried to change volume in "Sound Preferences" but it didn't work. I tried to boost mic via "alsamixer" but after the change the external mic doesn't work too! :'(
Does anyone know what happened? How can I fix it?[/INDENT]

---

### Post by amgmagician on 2010-09-18
The external microphone fixed by reconfiguring "pulseaudio":

```
sudo dpkg-reconfigure pulseaudio
```

but the internal one still has problem! :(

---

### Post by lidex on 2010-09-19
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by amgmagician on 2010-09-21
I uploaded information. The output link is:
[http://www.alsa-project.org/db/?f=9186803787c092ce023eba519b09095b6b204ae4](http://www.alsa-project.org/db/?f=9186803787c092ce023eba519b09095b6b204ae4)

---

### Post by lidex on 2010-09-22
> **amgmagician said:**
> I uploaded information. The output link is:
[http://www.alsa-project.org/db/?f=9186803787c092ce023eba519b09095b6b204ae4](http://www.alsa-project.org/db/?f=9186803787c092ce023eba519b09095b6b204ae4)

Try updating your alsa install via the link in my sig.

---

### Post by amgmagician on 2010-09-22
lidex,
[INDENT]I upgraded ALSA to version 1.0.23 according to the post you mentioned but my internal mic doen't work yet! :( Actually I follow these instructions:
```
1. download the script and save it somewhere
2. cd <your-download-dir>
3. tar xvf AlsaUpgrade-1.0.23-2.tar
4. sudo ./AlsaUpgrade-1.0.23-2.sh -d
5. sudo ./AlsaUpgrade-1.0.23-2.sh -c
6. sudo ./AlsaUpgrade-1.0.23-2.sh -i
7. sudo shutdown -r 0
```
[/INDENT]
[INDENT]Besides, I have a question. What's the relationship between alsa and pulseaudio. Is alsa a base of pulseaudio? How can I get more information about Ubuntu sound system?[/INDENT]

Thanks for your replies, lidex!

---

### Post by lidex on 2010-09-23
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

Then go to 'Sound Preferences' to select and unmute your mic in 'Input' tab.
Make sure you have selected a profile with 'duplex' or 'analog input' for the correct sound device on the 'Hardware' tab.
Use Pulse Audio Volume Control (pavucontrol) to unlock stereo sliders for the mic in 'Input Devices' tab. Drag the right slider down to zero. The mic is a mono device.

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

---

### Post by amgmagician on 2010-09-25
It seems it works! thanks a lot lidex! :D

---

### Post by sjv123 on 2010-09-25
> **amgmagician said:**
> Hi,

[INDENT]I have a T61 Thinkpad with Ubuntu 10.04. My internal mic didn't work however the external mic worked well. It seemed the input volume is low. In order to fix the internal mic problem I tried to change volume in "Sound Preferences" but it didn't work. I tried to boost mic via "alsamixer" but after the change the external mic doesn't work too! :'(
Does anyone know what happened? How can I fix it?[/INDENT]
I had a problem using the microphone on my headset to voice chat on G00GLE talk. I tried the gnome-alsamixer thing and pulse audio, to no avail.  I dont know if alsamixer and pulse audio were part of the solution, however I did some searching online and found this final step that worked for me.

I have to thank lidex  for pointing me in that direction in another post.

BTW:
My computer is a homebuilt desktop, using a gigabyte am3 board.  Apparently this fix works for systems using Realtek sound hardware.

step 1. Launch terminal and type " sudo gedit /etc/modprobe.d/alsa-base.conf "

step 2. Add "options snd-hda-intel position_fix=1"

Reboot and see if its working

---

