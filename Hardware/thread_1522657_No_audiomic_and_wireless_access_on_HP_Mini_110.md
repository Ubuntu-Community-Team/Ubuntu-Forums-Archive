---
title: "No audio/mic and wireless access on HP Mini 110"
date: 2010-07-02
forum: Hardware
---

### Post by rneube on 2010-07-02
I just installed Ubuntu in a new HP Mini, but I don't have sound, not even with external speakers, I can't record anything neither, and no wireless connections are detected even when the adapter is on. I was able to connect through a wired connection. 
I also performed all the updates and nothing.
I guess that this could be a driver's problem and HP doesn't support other OS than Windows.
Is there a solution to this problem or I just need to go  back to WIndows?

Thank you.

---

### Post by mozzwald on 2010-07-16
I just got the HP Mini 110-3015dx and installed 10.04 Netbook Edition. Wireless worked fine after removing network-manager and installing Wicd. Sound was detected, but no audio from the speakers, only the headphone jack. I fixed it with this:
```
sudo apt-get install linux-backports-modules-alsa-lucid-generic
```

You could try this for the wireless:
```
sudo apt-get install linux-backports-modules-wireless-lucid-generic
```

OR what I did:
```
sudo apt-get remove network-manager network-manager-gnome
sudo apt-get install wicd
```

---

### Post by jremington on 2010-07-31
After installation of Ubuntu 10.04 on my Mini 1110nr, the speaker sound was OK, but wireless was not. The above fix did not work for the wireless problem. However, installing the Broadcom BW43 wireless driver from the special hardware drivers menu worked.

After installing the driver and rebooting, check functionality by typing the following command in the terminal window:

iwlist scanning

This should list all nearby wireless nodes.

I also entered the following in /etc/network/interfaces

auto wlan0
iface wlan0 inet dhcp
wireless-essid ANY

and rebooted. This found my local unencrypted network and connected to it without any further problems.

Hope this helps! Jim

EDIT 8/10:  The bw43 wireless driver seems unreliable and sometimes puts the wireless chipset into a non-responsive state. After a number of attempts I gave up on Ubuntu 10.04 and went back to HP's MIE, which is actually a full-featured version of Ubuntu 8.x 

 Perhaps HP could donate their wireless driver to the Ubuntu community, in return for using Ubuntu in their product.

---

### Post by jremington on 2010-07-31
PS: The microphone does not seem to work, evening after trying the ALSA fix described above.

---

### Post by lidex on 2010-08-01
> **jremington said:**
> PS: The microphone does not seem to work, evening after trying the ALSA fix described above.

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

Then go to 'Sound Preferences' to select and unmute your mic in 'Input' tab. Use Pulse Audio Volume Control (pavucontrol) to unlock stereo sliders for the mic in 'Input Devices' tab. Drag the right slider down to zero. The mic is a mono device.

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

