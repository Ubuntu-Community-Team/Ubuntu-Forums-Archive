---
title: "Toshiba Satellite A665 Webcam and Microphone are not working with Ubuntu 10.04"
date: 2011-01-04
forum: Hardware
---

### Post by marcogh79 on 2011-01-04
Hi everybody!

I have a **Toshiba Satellite A665** laptop with [COLOR=Black]Ubuntu 10.04-32bit[/COLOR].
Since I have installed it, I can't make neither the integrated Webcam, nor the internal Microphone work. I guess the drivers are not installed.
Where can I find them, if they exist?
With the OS previously installed, Windows7-64bit, they did work fine.

Thanks!!

---

### Post by lidex on 2011-01-04
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

No joy? Need more info. Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by marcogh79 on 2011-01-14
Hi lidex and thanks for your answer!
I tried what you suggested me for the microphone, but i couldn't make it work. When I try to record a sound with the sound recorder, all I get is noise, I think white noise.

About the webcam, instead, I made some progress. Using the software 'Cheese' I can actually acquire videos and it works fine. What does not work is the video with skype. The skype version for Ubuntu doesn't seem to allow video calls, and the 'normal' skype 5.0, installed on Windows XP using the virtual machine, doesn't allow it neither. It only works when i reboot the computer in windows7.

bye
marco

---

### Post by lidex on 2011-01-15
Can you run the script at the bottom of my last post - it provides a wealth of info.

---

### Post by marcogh79 on 2011-01-18
ok, I tried it. It tells me to tell you that all the informations have been uploaded at:
[http://www.alsa-project.org/db/?f=53b57b3f6ff82e6498419150beed16f0e79e7da3](http://www.alsa-project.org/db/?f=53b57b3f6ff82e6498419150beed16f0e79e7da3)

---

### Post by lidex on 2011-01-19
Probably the easiest thing to do right now is upgrade your alsa-driver-modules. Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

### Post by marcogh79 on 2011-01-21
It works!
The problem was that the correct sound card was not selected (even if the loudspeakers were already working fine, I don't know why).
Once I opened Alsamixer via Terminal, I pressed F6 to select the sound card device. Three options appeared:
1) Default device
2) Intel device
3) NVidia device.

I selected the second one, the Intel, and it worked. With the first and the third it doesn't work. 

Thank you very much!
bye

---

### Post by marcogh79 on 2011-01-21
...about the Webcam, instead, the problem is that with Cheese it works fine, but with Skype, installed in Windows XP on Virtualbox, it doesn't work. Skype tells that no camera is detected.
I checked in Cheese's preferences: the internal Webcam is called " Webcam USB 2.0 (/dev/video0) "
How can I make the Virtualbox find it? and *pass* it to Windows XP and than to Skype?

---

### Post by Anoopsmohan on 2011-09-24
I have Toshiba satellite c660 laptop. Its speakers work properly, but headphone not working with ubuntu 10.04. At the same time headphone properly work with windows 7. But it is not useful for me, because iam an opensource programmer. Its alsamixer report located at [http://www.alsa-project.org/db/?f=5eb219a7881a25f183ffcea0a55341d027351bf9](http://www.alsa-project.org/db/?f=5eb219a7881a25f183ffcea0a55341d027351bf9)  If anybody can found the solution for this problem., please inform me..please help me..

---

