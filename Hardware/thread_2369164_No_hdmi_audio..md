---
title: "No hdmi audio."
date: 2017-08-19
forum: Hardware
---

### Post by vict00r2 on 2017-08-19
```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Analog is working fine.

I have spent hours trying to solve the problem. How to fix?

This is a fresh install for kodi running without a desktop environment. 

Spdif is unmuted in alsamixer.

[http://www.alsa-project.org/db/?f=69f4e63470c4e008f11dc8062021027a67af94d4](http://www.alsa-project.org/db/?f=69f4e63470c4e008f11dc8062021027a67af94d4)

---

### Post by ajgreeny on 2017-08-19
Have you checked the output devices in pulseaudio-volume-control? Perhaps the HDMI output is muted.

---

### Post by Autodave on 2017-08-19
Have you installed any driver for the video card? The default driver never gives me HDMI output option.  Go to Settings -> Additional drivers  and let it search for one. Install the recommended one. Reboot. Now, you should have HDMI output and will see it in pulse audio control.

---

### Post by vict00r2 on 2017-08-19
Thank you for helping.

Pulseaudio is not installed.
A desktop environment is not installed (can't go to Settings -> Additional drivers). 
I have the "nvidia-current" driver installed and I can see a Nvidia logo flashing on the screen when kodi starts.

---

### Post by Autodave on 2017-08-19
Sorry: I didn't read that as well as I should have. From the command line, someone else will have to jump in here.

---

### Post by vict00r2 on 2017-08-19
No problem. I have now installed Xubuntu-desktop.

Settings-Additional Drivers is showing "This device is using the recommended driver" (nvidia binary driver).

pavucontrol has no hdmi option, "Digital stereo (IEC958) Output" is present, unmuted. There's no sound on tv/hdmi when spdif is selected.

---

### Post by Autodave on 2017-08-19
The HDMI output enabling (at least on every Nvidia card that I have seen) is in the setup for the video card first. Once it iks enabled there, then ALSA will find it and make it an option for an output. What Nvidia video card is in there?

---

### Post by vict00r2 on 2017-08-19
This is old hardware, NVIDIA GeForce 6150 LE / nForce 430. The graphics chip is integrated in the motherboard.

From what I can tell, on this hardware, audio is supposed to play through hdmi when spdif is selected.

---

### Post by Autodave on 2017-08-20
That evidently is quite old: Nvidia's site lists drivers for that for Win95!  Unfortunately, it lists no Linux drivers. I'm sorry, but I am lost now. Perhaps someone else here can help.

---

### Post by vict00r2 on 2017-08-20
I think you didn't read as well as you should have again. :)

I have no problem finding the linux driver for this graphics card on Nvidia's site.

---

### Post by Autodave on 2017-08-20
What driver do you have installed then? I see none listed. I see a lot of info about sound, but nothing about video.

Understand: I am NOT the best person to read through all of that and tell you that I know what it means. However, I have read through it 3 times and I cannot find anything pertaining to video.

The option to turn on sound via HDMI comes through the video driver.

---

### Post by vict00r2 on 2017-08-20
Only clue is "nvidia" is listed in loaded modules.

This graphics card probably does not have its own internal audio codec -> no option to turn on HDMI audio from the video driver(?). Audio should be routed from the spdif output of the soundcard to the graphics card.

Video driver is "304.135":

```
$ cat /proc/driver/nvidia/version 
NVRM version: NVIDIA UNIX x86_64 Kernel Module  304.135  Tue Jan 17 15:26:26 PST 2017
GCC version:  gcc version 5.4.0 20160609 (Ubuntu 5.4.0-6ubuntu1~16.04.4)

$ nvidia-smi | grep Version
| NVIDIA-SMI 4.304...   Driver Version: 304.135        |                       

$ lsmod | grep nvidia
nvidia              11407360  31
drm                   364544  3 nvidia

```

---

### Post by vocx on 2017-08-20
> **vict00r2 said:**
> Only clue is "nvidia" is listed in loaded modules.

This graphics card probably does not have its own internal audio codec -> no option to turn on HDMI audio from the video driver(?). Audio should be routed from the spdif output of the soundcard to the graphics card.

Video driver is "304.135":

```
$ cat /proc/driver/nvidia/version 
NVRM version: NVIDIA UNIX x86_64 Kernel Module  304.135  Tue Jan 17 15:26:26 PST 2017
GCC version:  gcc version 5.4.0 20160609 (Ubuntu 5.4.0-6ubuntu1~16.04.4)

$ nvidia-smi | grep Version
| NVIDIA-SMI 4.304...   Driver Version: 304.135        |                       

$ lsmod | grep nvidia
nvidia              11407360  31
drm                   364544  3 nvidia

```
Take a look at some threads
[https://ubuntuforums.org/showthread.php?t=2368156&p=13673996#post13673996](https://ubuntuforums.org/showthread.php?t=2368156&p=13673996#post13673996)
[https://ubuntuforums.org/showthread.php?t=2367135&p=13670073#post13670073](https://ubuntuforums.org/showthread.php?t=2367135&p=13670073#post13670073)

There are several reports where the audio through HDMI doesn't work correctly. These problems seem to affect Nvidia cards (discrete) paired with Intel graphics (integrated). I'm still not quite sure.

I seem to experience a similar problem. I have a discrete Nvidia card with the 375 driver, but apparently my sound card is the Intel HDMI device, not the Nvidia device like in your case. So, the problem could be in the Intel driver for me (i915), or the Nvidia driver (375 for me, 340 for you), or somewhere else (alsa, pulseaudio, kernel?). It is a bit difficult to troubleshoot.

---

### Post by Autodave on 2017-08-20
With that driver, you should be OK. Hook up the HDMI cable to the PC and the TV. Boot or reboot Linux. Now go into pavucontrol -> Output devices. From there, you should be able to chose one of the dropdown menus and chose HDMI as one of the outputs. You may have to unmute it.

---

### Post by Yellow Pasque on 2017-08-20
Your video driver info looks fine.

So do you have an MSI Media Live? This is about the closest thing I could find: [https://lists.gt.net/mythtv/users/337532](https://lists.gt.net/mythtv/users/337532)

> From what I can tell, on this hardware, audio is supposed to play through hdmi when spdif is selected. 

I find that odd considering the system (if we are talking about Media Live) also has Digital Audio Out jacks. Like there should be a setting in alsamixer to differentiate between them. Maybe not though. Maybe signal goes to both.

---

### Post by vict00r2 on 2017-08-21
> **Autodave said:**
> With that driver, you should be OK. Hook up the HDMI cable to the PC and the TV. Boot or reboot Linux. Now go into pavucontrol -> Output devices. From there, you should be able to chose one of the dropdown menus and chose HDMI as one of the outputs. You may have to unmute it.

Still no HDMI option in pavucontrol.

> **Temüjin said:**
> 
So do you have an MSI Media Live? This is about the closest thing I could find: [https://lists.gt.net/mythtv/users/337532](https://lists.gt.net/mythtv/users/337532)

I find that odd considering the system (if we are talking about Media Live) also has Digital Audio Out jacks. Like there should be a setting in alsamixer to differentiate between them. Maybe not though. Maybe signal goes to both.

I don't have the Media Live but this motherboard is identical to the one in that box.

As described in that link audio on hdmi should work when selecting spdif in alsa.

Looking at dmesg could the bold text indicate a setting to differentiate?

```
[    7.720082] snd_hda_codec_realtek hdaudioC0D0: autoconfig for ALC883: line_outs=1 (0x1b/0x0/0x0/0x0/0x0) type:hp
[    7.720090] snd_hda_codec_realtek hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    7.720094] snd_hda_codec_realtek hdaudioC0D0:    hp_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    7.720096] snd_hda_codec_realtek hdaudioC0D0:    mono: mono_out=0x0
**[    7.720099] snd_hda_codec_realtek hdaudioC0D0:    dig-out=0x1e/0x0**
[    7.720101] snd_hda_codec_realtek hdaudioC0D0:    inputs:
[    7.720105] snd_hda_codec_realtek hdaudioC0D0:      Mic=0x19
[    7.720107] snd_hda_codec_realtek hdaudioC0D0:    dig-in=0x1f
[    8.058242] IPv6: ADDRCONF(NETDEV_UP): enp0s20: link is not ready
[    8.059159] forcedeth 0000:00:14.0 enp0s20: no link during initialization
[    8.060362] IPv6: ADDRCONF(NETDEV_UP): enp0s20: link is not ready
[    8.857193] input: HDA NVidia Mic as /devices/pci0000:00/0000:00:10.1/sound/card0/input7
[    8.857293] input: HDA NVidia Front Headphone as /devices/pci0000:00/0000:00:10.1/sound/card0/input8
```

---

### Post by Yellow Pasque on 2017-08-22
Did you do as the link suggested and update the BIOS, and look for the 'Disable 8ch audio' option in BIOS?

The line in bold just gives the pin number for the digital output.

---

### Post by vict00r2 on 2017-08-22
Yes, I have tried both BIOS v1.61 and v1.63, 8 channel audio disabled  and enabled. It makes no difference. There's no hdmi audio.

I have now decoded EDID from the tv:

```
Audio data block
  Linear PCM, **max channels 1**
  Supported sample rates (kHz): 48 44.1 32
  Supported sample sizes (bits): 24 20 16

```

Assuming signal goes to hdmi when playing audio on spdif, the result is likely a channel count mismatch. At the moment I'm hoping that this is the issue.

Any feedback on this or other thoughts is appreciated.

---

