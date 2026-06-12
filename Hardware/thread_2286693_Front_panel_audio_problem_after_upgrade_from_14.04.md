---
title: "Front panel audio problem after upgrade from 14.04 LTS to 15.04"
date: 2015-07-14
forum: Hardware
---

### Post by gmlucian78 on 2015-07-14
hello,
Could someone help me solve this problem:

Before upgrading from Ubuntu 14.04 LTS to 15.04  all went well on my computer. 

When inserting headphone on front panel the audio from speaker inserted in back was muted. Now there is no sound on front panel.

I am using the following work around:

Whenever I need to listen to headphone
 
[LIST]
[*]I start a terminal window 
[*]. I start Alsamixer. 
[*]I press f6 to change sound card from HDA Intel HDMI to HDA Intel PCH. 
[*]I change the volume of headphone and master sound and all works until next reboot. 
[/LIST]
 
Here is the output from the command:

```
wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) && bash ./alsa-info.sh --upload;
```

[http://www.alsa-project.org/db/?f=05f8cb503d52a211cdb87788aca5925ba7091058](http://www.alsa-project.org/db/?f=05f8cb503d52a211cdb87788aca5925ba7091058)


I want to save all those settings .

Thank you for your time!


[B]UPDATE 29/07/2015

Output from command
 ```
aplay -l
```[/B]
> **** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA Intel HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
uname -r
```
> 3.19.0-23-generic

I have installed oem-audio-hda-daily-lts-vivid-dkms with the following command:
```
 sudo apt-get install oem-audio-hda-daily-lts-vivid-dkms
```

Front audio from headphones still didn't worked.

I have uninstalled oem-audio-hda-daily-lts-vivid-dkms using the command:

```
sudo apt-get remove oem-audio-hda-daily-dkms
```

Other commands used on my machine:
```

uname -a
```
> Linux wxxxwss 3.19.0-23-generic #24-Ubuntu SMP Tue Jul 7 18:52:55 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```
echo $PATH
```
> /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games

I have tryied even the solution from this post [http://ubuntuforums.org/showthread.php?t=1652691](http://ubuntuforums.org/showthread.php?t=1652691) but still didn't worked.

For now the only solution that enables me to hear sound from front panel through headphones is the one presented in the work around.

---

