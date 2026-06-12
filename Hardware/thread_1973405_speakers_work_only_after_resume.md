---
title: "speakers work only after resume"
date: 2012-05-04
forum: Hardware
---

### Post by mmicotti on 2012-05-04
Hi 

since the 11.10 version of Ubuntu I have this problem: when I start my notebook, speakers do not work, whereas headphones do.
After standby and resume, usually but not always, everything works well.
Any ideas?

Thanks!

some information about my notebook

Ubuntu 12.04 LTS 64bit (fresh installation)
HP Elitebook 8440p 

the output of aplay -l is the following: 

```
**** Lista di PLAYBACK dispositivi hardware ****
scheda 0: Intel [HDA Intel], dispositivo 0: STAC92xx Analog [STAC92xx Analog]
  Sottoperiferiche: 0/1
  Sottoperiferica #0: subdevice #0
scheda 1: NVidia [HDA NVidia], dispositivo 3: HDMI 0 [HDMI 0]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 1: NVidia [HDA NVidia], dispositivo 7: HDMI 0 [HDMI 0]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 1: NVidia [HDA NVidia], dispositivo 8: HDMI 0 [HDMI 0]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 1: NVidia [HDA NVidia], dispositivo 9: HDMI 0 [HDMI 0]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
```

---

### Post by mmicotti on 2012-05-18
Finally I fixed it.

I followed the instruction of the last post of this thread: [http://www.linux-archive.org/gentoo-user/566518-ff-chromium-trapped-deafness-how-configure-alsa-correctly.html ]("http://www.linux-archive.org/gentoo-user/566518-ff-chromium-trapped-deafness-how-configure-alsa-correctly.html")(linked by this other one:[ http://www.linuxquestions.org/questions/slackware-14/slackware-13-37-audio-setup-seems-fine-no-sound-922521/]("http://www.linuxquestions.org/questions/slackware-14/slackware-13-37-audio-setup-seems-fine-no-sound-922521/")), and I set the last line of alsa-base.conf as follows:

```
options snd-intel-hda model=auto,auto enable_msi=1,0 index=0,1 id=Intel,NVidia
```


After shutdown (simply rebooting do not work, I don't know why) everything seems to work fine..

---

