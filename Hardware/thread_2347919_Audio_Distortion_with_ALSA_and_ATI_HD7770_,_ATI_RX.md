---
title: "Audio Distortion with ALSA and ATI HD7770 , ATI RX460 Cards"
date: 2016-12-29
forum: Hardware
---

### Post by vmstek on 2016-12-29
ALSA Info  -  [http://www.alsa-project.org/db/?f=060eee8e6e20933f414a4cdb0361a4a980a598ab](http://www.alsa-project.org/db/?f=060eee8e6e20933f414a4cdb0361a4a980a598ab)

This problem has completely spoiled my holidays, so I am turning to the community for help.

I have a Ubuntu standalone minimal server I use for an HTPC with Kodi.
With the ATI HD7770 and RX460 video cards (using the HDMI connection to an AVR) I get a repeating audio distortion.
Where there should be 1 gui menu "click" , there are several. This translates to a crackling distortion in all soundtracks. (AC3, DTS, DD, etc.) 

I have tried OS versions 14.04, 15.04, 16.04 and 17.0., as well as Kodi 16, 17b and 18 alphas. Always the same problem
I have tried the Radeon driver, and the AMDGPU Pro driver.
With an NVidia card (GT610) I do not have the problem.
With PulseAudio, I do not have the problem...but Kodi only supports 2 channel audio with PulseAudio.

My old ATI HD5770 never had this problem, but support for it has been discontinued.

My ALSA info log are in the first line of this post.

HELP!! please...

---

### Post by Yellow Pasque on 2016-12-30
You can try the position_fix=1 trick: [https://wiki.ubuntu.com/Audio/PositionReporting](https://wiki.ubuntu.com/Audio/PositionReporting)

> My old ATI HD5770 never had this problem, but support for it has been discontinued

False. Radeon driver should support it just fine. Video playback should work well as long as mesa-vdpau-drivers is installed and Kodi is set to use vdpau output.

---

### Post by vmstek on 2016-12-30
Tried both those settings it did not help.
HD5770 is not supported Ubuntu 16.04, according to the AMD driver site.
I purged Alsa, and still had the problem in Kodi, so I guess it is not an ALSA issue.
Even switched out the cables.

Update: Put the HD5770 back in, and all is good again.
Main difference seems to be that the HD7770 and Rx460 are detected as having 6 HDMI sound inputs, and the HD5770 is detected as 1 HDMI sound input.
Both cards have 1 HDMI port and 1 DP.

[   16.204637] snd_hda_intel 0000:01:00.1: Handle VGA-switcheroo audio client
[   16.204642] snd_hda_intel 0000:01:00.1: Force to non-snoop mode
[   16.204685] snd_hda_intel 0000:01:00.1: irq 45 for MSI/MSI-X
[   16.264539] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card0/input3
[   16.265711] input: HDA ATI HDMI HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card0/input4
[   16.267527] input: HDA ATI HDMI HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card0/input5
[   16.267625] input: HDA ATI HDMI HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card0/input6
[   16.267716] input: HDA ATI HDMI HDMI/DP,pcm=10 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card0/input7
[   16.267804] input: HDA ATI HDMI HDMI/DP,pcm=11 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card0/input8
[   16.431149] [drm] radeon kernel modesetting enabled.
--
[   18.266521] [drm] Connector 1:
[   18.266522] [drm]   HDMI-A-1
[   18.266523] [drm]   HPD4

Must be a way to disable those somehow...

---

