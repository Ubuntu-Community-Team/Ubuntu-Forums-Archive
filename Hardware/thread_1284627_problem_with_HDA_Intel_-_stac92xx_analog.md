---
title: "problem with HDA Intel - stac92xx analog"
date: 2009-10-06
forum: Hardware
---

### Post by matessso on 2009-10-06
A while ago I installed ubuntu linux on my laptop. On windows vista home premium everything works perfect ( I mean the hardware) but on the linux i don't hear any sound. It says that it uses a HDA Intel - stac92xx device. I tried to google it and found many similar problems and many solutions but non seem to work due to that I m not really good at working with linux and I don't know when they say for example to do  "options snd-hda-intel enable_msi=1" in /etc/modprobe.d/alsa-base." Can someone help me please? Thanks!

I have attached a photo of alsamixer with card info

---

### Post by matessso on 2009-10-07
I also have HDA ATI HDMI and sound doesn't work on it either

---

### Post by helpdeskdan on 2009-10-09
Me too.  Worked great in Hardy, I wish I had never upgraded.  Yeah, I tried that, looked up my card and added:
options snd-hda-intel model=dell-3stack
Even installed new Alsa.  No joy. 
 
I've had some luck going to oss4, as have others with this card.  Instructions are here:

[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

However, I'm not having any luck (yet) with recording.  One of us should purchase support for oss4 so we can get sound recording working!

---

### Post by helpdeskdan on 2009-10-09
Finally got it working.  The line is "options snd-hda-intel model=ref"

Open up a console and type this:

sudo gedit /etc/modprobe.d/alsa-base.conf

Add that line, reboot, and hopefully you'll have sound!

---

### Post by anectine17 on 2009-11-12
Thanks!! That did the trick!!

---

### Post by mshamma on 2010-03-22
Worked for me too.

---

### Post by ajmctaggart on 2010-05-24
Worked for me too!

Dell Latitude E6510 Ubuntu 10.04
Mic was not working via Alsa or Pulse Audio

```
XXXX~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I tried EVERYTHING- including upgrading to the latest Alsa via:
[http://ubuntuforums.org/showthread.php?p=6589810#post6589810]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810")

And this is the ONLY thing that worked!

I did have to go to the terminal:
```
 gstreamer-properties 
```
Make sure all audio settings are set to Alsa.

I used Sound Recorder for testing purposes.

I also made sure the sound preferences via the volume icon or the System>Preferences>Sound for the card were set to Digital Output and Analog Input.

Many, many thanks- I bought a Dell Latitude in hopes of running Ubuntu as my daily OS.

---

### Post by bach on 2010-07-04
I am running Ubuntu 10.04 on a DELL 6510 notebook. Sound works, but mic does not. The above hint did not work for me. I did

gstreamer-properties

and chose Alsa. However, I am unable to record sounds. Mic does work in Skype either. 

Tips are mostly welcome. Thanks.

---

### Post by lidex on 2010-07-05
> **bach said:**
> I am running Ubuntu 10.04 on a DELL 6510 notebook. Sound works, but mic does not. The above hint did not work for me. I did

gstreamer-properties

and chose Alsa. However, I am unable to record sounds. Mic does work in Skype either. 

Tips are mostly welcome. Thanks.

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

Then use pulseaudio volume control (pavucontrol) to select your mic in 'Input Devices' tab.

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

### Post by bronxien on 2010-12-26
Okay hi guys I'm having a bit of a problem here. I too have this sound card but don't really know if it's the card I'm having with. Basically I have absolutely no sound. now I followed the Instruction with the whole editing of the "options" whatever in alsa-base file. is it that I should delete what i have there then paste whatever. I changed whatever i had in the file to this:

options snd-C index=0
options snd-A index=1
options snd-B index=2

I really need some help you guys have no idea how many things I've done just to get sound.
My laptop is a HP Compaq which uses the hda-intel. It's also on dual boot with windows 7.

---

### Post by lidex on 2010-12-26
@bronxien
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by Good_Newz on 2011-05-23
> **helpdeskdan said:**
> Finally got it working.  The line is "options snd-hda-intel model=ref"

Open up a console and type this:

sudo gedit /etc/modprobe.d/alsa-base.conf

Add that line, reboot, and hopefully you'll have sound!

For those of you that the above didnt work you can try this: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto). Mine dell laptop sound and mic only worked with dell-m6-dmic (instead of ref). None of the other options worked for me. Follow the instructions and by trial and error you might hit the one that works. :)

---

### Post by koxa on 2012-01-17
Hi all.
Followed all instructions. My sound still not working.
Running Ubuntu Server last version.
This is my output: [http://www.alsa-project.org/db/?f=edd6c821a96a9b50a4893d45c97558dc6a6cb91b](http://www.alsa-project.org/db/?f=edd6c821a96a9b50a4893d45c97558dc6a6cb91b)

Help plz!

my laptop is Dell Latitude 5420

---

### Post by koxa on 2012-01-19
Help plz!

---

### Post by MoreOrLess on 2012-01-19
@koxa: That's a really new codec. You probably need the latest alsa kernel module. Try the oneiric .deb from here: [https://code.launchpad.net/~ubuntu-audio-dev/+archive/alsa-daily/+packages](https://code.launchpad.net/~ubuntu-audio-dev/+archive/alsa-daily/+packages)

---

