---
title: "Toshiba Satellite A665-s6056 internal mic not working, Ubuntu 10.04"
date: 2011-04-17
forum: Hardware
---

### Post by Hallic7 on 2011-04-17
Hi! I installed Ubuntu 10.04 a few days ago and everything seems to work fine except the built-in mic. I discovered something was wrong because the mic in Skype did not work.
I went to "Sound Preferences" and in the "Input" tab I unchecked the mute box but still does not work. 
Any ideas on how to get it working?

---

### Post by lidex on 2011-04-17
Mic Problem

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

---

### Post by Hallic7 on 2011-04-18
Thanks for the fast reply!
I tried all the steps mentioned and all seems to be in order but no mic functionality yet.
What else can I do?
Thanks!

---

### Post by Marcelo Ruiz on 2011-04-18
Check this:

[http://ubuntuforums.org/showthread.php?t=1701900]("http://ubuntuforums.org/showthread.php?t=1701900")

It worked in my Qosmio. Please post results so others can follow/avoid recommendation based on your success.

---

### Post by Hallic7 on 2011-04-18
Hi! Marcelo thanks for your reply.
I added the two lines of code to the "alsa-base.conf" but still is not working...
Any more ideas?

---

### Post by Hallic7 on 2011-04-21
Ideas please... Because of this I can't use Ubuntu all the time and have to switch with windows for skype :(

---

### Post by lidex on 2011-04-21
Anything you added to alsa-base.conf please remove and reboot. Next use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by Hallic7 on 2011-04-23
Lidex thanks for replying, this is the link provided by the script...

[http://www.alsa-project.org/db/?f=31ce203c59148d57c3edc061843fe885886fdb82](http://www.alsa-project.org/db/?f=31ce203c59148d57c3edc061843fe885886fdb82)

I hope this information is useful!

Thanks a lot!!

---

### Post by lidex on 2011-04-24
Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=auto" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**
Try sound recorder next - if the mic works there, it's a skype issue.

---

### Post by Hallic7 on 2011-04-25
Hi Lidex, I tried your code, but still the mic is not working :( Any other suggestions? 

Thanks for your patience!!!

---

### Post by lidex on 2011-04-27
Does the mic work with sound recorder?
What version of skype? 2.1 or 2.2?

---

### Post by Hallic7 on 2011-05-01
Hi!!! the mic does not work with sound recorder :(
My Skype version is 2.2.0.25

Ideas?

Thanks in advance!!

---

### Post by lidex on 2011-05-01
Changing default subdevice configuration

   >  Some sound devices have multiple capture subdevices (eg. hda-intel), but pulseaudio only seems to detect the parent device, and only listens to subdevice #0. ALSA may not be configured to use your preferred device as subdevice #0 by default.

        Open the pulseaudio record meter (pavumeter --record)
        Talk into your chosen device while you carry out the process and watch the meter.
            Some channels are quite noisy even with no input (especially on integrated chipsets), so we are watching for movements that correspond to our voice. 

        Use alsamixer -c n (where n is your sound card number, probably 0)
            Press F4 to get to the capture console
            Make sure the first capture channel is enabled ("CAPTUR" in red, press space to toggle), and the volume turned up.
            Check the first input source is switched to your chosen plug (Mic, in my case) 
        At this point, you should see the record meter bouncing in response to your voice.
        I found that I had to repeat this procedure each time I wanted to use the Mic, even though the settings "stuck" in the mixer, something in the soundcard wasn't initialized until it was repeated.
        This also works if you use the "Options" tab in the standard mixer app to do the same thing. 

---

### Post by c.parin on 2011-11-16
Hi, I am using Toshiba Satellite C660 I-5010 and Ubuntu 10.04. I'am having the same problem of internal mic not working. I've tried the solutions posted on this thread in vain. When I connect an external headphones (with mic), still it is not working.
please help...
Thank you for your time.

---

