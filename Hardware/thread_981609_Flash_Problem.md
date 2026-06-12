---
title: "Flash Problem"
date: 2008-11-13
forum: Hardware
---

### Post by Gndoab on 2008-11-13
Hi, I just installed 8.10, and for the first time, almost everything works. The only thing I am having problems with is that flash in firefox is using my laptops built in speakers-sound card, when I have the sound settings set up to use my external sound blaster usb. There is no option under the settings menu when I right click on a flash app to change what device it is using. Anyone know what to do?

---

### Post by kostkon on 2008-11-13
> **Gndoab said:**
> Hi, I just installed 8.10, and for the first time, almost everything works. The only thing I am having problems with is that flash in firefox is using my laptops built in speakers-sound card, when I have the sound settings set up to use my external sound blaster usb. There is no option under the settings menu when I right click on a flash app to change what device it is using. Anyone know what to do?
You will need to install the *PulseAudio Device Chooser* (the package is called *padevchooser*).

It will create an menu entry in *Applications -> Sound & Video*. Run it and it will put its icon in your taskbar. Left-click on it and select the *Volume Control* option.

Run a *Flash* video and in the first tab (*Playback*) you should see its stream. Right-click on it and select *Move Stream...* A list will appear and it should list all of audio devices (in your case your internal soundcard that uses the laptop's speakers and your external USB card). Select the device you want *Flash* to use to output its sound. From now on, *PulseAudio* will remember your option and always send the audio from *Flash* to the device you have chosen.

Thus, you get great flexibility of choosing the audio device that any application in your system to output its sound.

In the *Volume Control*, in the *Output Devices* tab you should see your audio devices listed. You can right-click on the one you want to set as the default and enable the *Default* option that appears.

You can set the *PulseAudio Device Chooser* to start every time you login from its preferences (i.e. left-click on its icon and select *Preferences*).

Hope you like it! :)

---

