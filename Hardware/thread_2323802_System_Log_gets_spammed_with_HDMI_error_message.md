---
title: "System Log gets spammed with HDMI error message"
date: 2016-05-08
forum: Hardware
---

### Post by j4GGy on 2016-05-08
Hi guys,

first let me say that although I have a few years experience with hardware and coding, when it comes to Linux/Ubuntu I'm more on the newb-ish side of things. So please be accurate on where to find stuff when asking for contents of log files or smth.

Now the problem: I'm running Ubuntu 16.04 32-bit on an ACER TravelMate 8473 (Intel® Core™ i5-2430M, 4GB RAM, integrated Intel Graphics with additional NVIDIA Geforce GT 540M) and the system seems to be running quite smoothly with the only caveat being that my System Log looks like this:

```

May  8 16:13:43 TW-Laptop kernel: [ 3654.130528] snd_hda_codec_hdmi hdaudioC1D3: Unable to sync register 0x4f0d00. -5
May  8 16:13:43 TW-Laptop kernel: [ 3654.130533] snd_hda_codec_hdmi hdaudioC1D3: HDMI: invalid ELD buf size -1
May  8 16:13:43 TW-Laptop kernel: [ 3654.130538] snd_hda_codec_hdmi hdaudioC1D3: HDMI: invalid ELD buf size -1
May  8 16:13:43 TW-Laptop kernel: [ 3654.262471] snd_hda_codec_hdmi hdaudioC1D1: Unable to sync register 0x4f0d00. -5
May  8 16:13:43 TW-Laptop kernel: [ 3654.262497] snd_hda_codec_hdmi hdaudioC1D1: HDMI: invalid ELD buf size -1
May  8 16:13:43 TW-Laptop kernel: [ 3654.262506] snd_hda_codec_hdmi hdaudioC1D1: HDMI: invalid ELD buf size -1
May  8 16:13:43 TW-Laptop kernel: [ 3654.430428] snd_hda_codec_hdmi hdaudioC1D3: Unable to sync register 0x4f0d00. -5
May  8 16:13:43 TW-Laptop kernel: [ 3654.430440] snd_hda_codec_hdmi hdaudioC1D3: HDMI: invalid ELD buf size -1
May  8 16:13:43 TW-Laptop kernel: [ 3654.430446] snd_hda_codec_hdmi hdaudioC1D3: HDMI: invalid ELD buf size -1
May  8 16:13:43 TW-Laptop kernel: [ 3654.430460] snd_hda_codec_hdmi hdaudioC1D2: Unable to sync register 0x4f0d00. -5
May  8 16:13:43 TW-Laptop kernel: [ 3654.430463] snd_hda_codec_hdmi hdaudioC1D2: HDMI: invalid ELD buf size -1
May  8 16:13:43 TW-Laptop kernel: [ 3654.430467] snd_hda_codec_hdmi hdaudioC1D2: HDMI: invalid ELD buf size -1
May  8 16:13:43 TW-Laptop kernel: [ 3654.430479] snd_hda_codec_hdmi hdaudioC1D0: Unable to sync register 0x4f0d00. -5
May  8 16:13:43 TW-Laptop kernel: [ 3654.430483] snd_hda_codec_hdmi hdaudioC1D0: HDMI: invalid ELD buf size -1
May  8 16:13:43 TW-Laptop kernel: [ 3654.430487] snd_hda_codec_hdmi hdaudioC1D0: HDMI: invalid ELD buf size -1

```

As you can see, these errors seem to be thrown roughly every 0.2 seconds or so which makes me worry that it may impact the overall performance of my system. Also, errors are never good, are they?

My suspicion regarding the origin of these errors is the following: I'm using the proprietary Nvidia driver 361.42 (nvidia-361) and nvidia-settings to turn my dedicated graphics card off. I don't really use it much and would not care about it if my HDMI output wasn't hardwired to it. So in order to stream anything onto my TV, I have to use the Nvidia card. If I activate the Nvidia card, the error messages stop. So my guess is that some audio service (ALSA or smth?) tries to access the HDMI port even if the Nvidia card is turned off, fails, and thus fires a motherload of error messages. However, I have no clue how to tell whatever service is causing this errors to ignore the HDMI audio output while the Nvidia card is turned off.

Any ideas/help is deeply appreciated!

---

### Post by deadflowr on 2016-05-08
*Thread moved to **Hardware**.*

---

### Post by j4GGy on 2016-05-13
For completeness, let me post the output of lspci and aplay:

** lspci | grep -i audio**
```
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
01:00.1 Audio device: NVIDIA Corporation GF108 High Definition Audio Controller (rev ff)
```

** aplay -l**
```

**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: CX20588 Analog [CX20588 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Now to the more interesting part. While the Nvidia card is turned off, the output of **cat /proc/asound/modules** is
```

 0 snd_hda_intel
 1 snd_hda_intel
```
so it seems that the snd-hda-intel driver is used for both the Intel sound chipset and the HDMI port (which I believe is hardwired to the NVidia card). Since I also got an error about invalid ELD, I used **cat** **/proc/asound/card1/eld*** and got
```
monitor_present        1
eld_valid        0
monitor_present        1
eld_valid        0
monitor_present        1
eld_valid        0
monitor_present        1
eld_valid        0
```
which is strange since I have nothing connected to the HDMI port. Hence, I believe that this ELD information does not get parsed/updated correctly which makes snd-hda-intel try to access some registers which are inaccessible if there is no monitor connected. Is this assessment correct and if so, how can I tell my system that there is nothing connected to the HDMI port? Manually writing "monitor_present 0" to eld#0.0 does not work as I get a "Permission denied" error even when in superuser mode.

Thanks in advance

---

### Post by Yellow Pasque on 2016-05-13
Try the latest upstream 4.6.x kernel. There have been recent changes to the ELD handling over the past few months, including:
[https://github.com/torvalds/linux/commit/bd48128539ab89986b24ad08ecd3e027dd1993a1](https://github.com/torvalds/linux/commit/bd48128539ab89986b24ad08ecd3e027dd1993a1)

[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.6-rc7-yakkety/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.6-rc7-yakkety/)

If you have success with the new kernel, please respond to:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1573864](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1573864)

---

