---
title: "Recover from Karmic Sound Changes"
date: 2009-11-30
forum: Hardware
---

### Post by pgn674 on 2009-11-30
I had Ubuntu 9.04 on my desktop and laptop, and recently upgraded both to 9.10. On both machines, the upgrade introduced problems in the sound management.

On my desktop, I can't get the Line In audio to go out to my speakers. I would like to do this because I like to have my MP3 player playing on my speakers, but I don't want to have to reach behind my computer to pull the cord to plug in my MP3 player. In 9.03, I think Line In was always directed to output, as long as it wasn't muted, but now I can't figure out any way to get it to work.

On my laptop, I can't get sound to go out the headphone jack without also coming out the internal speakers. Also, I can't get the microphone input to stop coming out either. In 9.04, with a little fiddling with the front and main sliders and mute buttons I could always get it to go out the headphones alone, and muting the microphone actually muted it from the speakers and headphones.

Is there any way to get the old audio system back, or at least its functionality? Or, am I looking in the wrong place for specifying audio direction? I have gone through System>Preferences>Volume Control completely on both computers, fiddling with everything, with no promising results. I have also search all over online, but everything I find is for older Ubuntu's, and 9.10 seems to be quite different.

---

### Post by mocha on 2009-12-02
I have the same problem.  It turns out that the new Karmic pulseaudio setup doesn't map to the same controls alsa has over the hardware.  One workaround to this is to install the gnome-alsa-mixer and use it only for adjusting the line-in and analog mix, or use the command line alsamixer "alsamixer -Dhw:0".

You can still use the Karmic pulseaudio stuff to adjust the capture level from the line-in.

---

### Post by pgn674 on 2010-02-22
Thanks for the hint. Using gnome-alsamixer, I was able to fix my desktop completely, and I was able to stop the mic on my laptop. However, I'm still having trouble separating my laptop's internal speakers from its headphone port.

GNOME ALSA Mixer lists the following sound card elements:```
(Sliders:)
Master
PCM
Front
Front Mic
Front Mic Boost
CD
Mic
Mic Boost
Capture
Beep
Digital
(Check boxes:)
Headphone
Input Source
```Fiddling with all of this doesn't help. If I uncheck Headphone, it mutes both internal speakers and the headphone port. Sliding any of the first three sliders changes both devices at the same time, too. It says I have a Realtek ALC861-VD sound card. This is a Lenovo 3000 C200 laptop.

If I start the PulseAudio Device Chooser, I can open the Volume Control through that. The Output Devices tab shows Internal Audio Analog Stereo has two ports: Analog Output, and Analog Headphones. Changing the volume level on either one changes the volume for both the internal speakers and the headphone port at the same time. The mute buttons do the same.

Does anyone have any more ideas? Or, is there any more info about my setup that might be helpful to know?

---

### Post by Yellow Pasque on 2010-02-22
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```
This should bring up a text file. Add this line:
```
options snd-hda-intel model=lenovo
```
Save. Quit. Reboot.

---

### Post by pgn674 on 2010-03-19
Thank you, that worked. It even automatically changes between headphones and internal speakers when I plug in or unplug my headphone cord.

---

