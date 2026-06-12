---
title: "Re: Realtek ALC298 - Ubuntu 16.04 - Audio and microphone not working"
date: 2017-12-05
forum: Hardware
---

### Post by emil-fresk on 2017-12-05
Hi, I am running Ubuntu 16.04 and have a similar issue: Only the microphone input is NOT working. 
I am using an **Xaomi Mi Notebook Pro**, which I am also guessing the author of the thread is using as we have exactly the same hardware.
```
grep "Codec:" /proc/asound/card*/codec* 

/proc/asound/card0/codec#0:Codec: Realtek ALC298
/proc/asound/card0/codec#2:Codec: Intel Kabylake HDMI

```

```
cat /proc/asound/cards 0 

 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xb4220000 irq 289

```

Has anyone got a fix for this?
I have no issues with the microphone in Windows, and I have no idea of how to debug this as the drivers for the Codecs seems to be working fine (especially with sound output working).

---

### Post by coffeecat on 2017-12-06
Post moved to own thread.

---

### Post by Yellow Pasque on 2017-12-06
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by olekr on 2017-12-18
Same issue, same laptop: Xiaomi Mi Notebook Pro - Realtek ALC298 - Ubuntu 16.04.03.  Audio playback works fine, mic does not work at all.  AlsaMixer does not even register the mic as an output.  Tried a whole bunch of stuff with PulseAudio GUI but nothing helped.

Found this:

[https://ubuntuforums.org/showthread.php?t=2363938](https://ubuntuforums.org/showthread.php?t=2363938)

which leads to:

[http://airbornesurfer.com/2015/04/how-to-install-realtek-hd-audio-driver-in-linux/](http://airbornesurfer.com/2015/04/how-to-install-realtek-hd-audio-driver-in-linux/)
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false)

If you download the latest Linux drivers from above you won't find 'ALC298' on the list of supported codecs so I am unsure if we can even compile an updated version of the Realtek drivers for this device. 

Here is my AlsaInfo:

[http://www.alsa-project.org/db/?f=9b52072f0df7478f6b8221b3b73694d4908724b5](http://www.alsa-project.org/db/?f=9b52072f0df7478f6b8221b3b73694d4908724b5)

---

### Post by Yellow Pasque on 2017-12-19
Do not touch Realtek's Linux audio driver. As you can see, it hasn't been updated in years and will not build correctly with modern kernels. Worse, it will still try and install and break your sound (as in the thread you linked).

When people want to update their audio driver, I point them here:
[https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

---

### Post by synoday on 2018-01-09
> **Temüjin said:**
> Do not touch Realtek's Linux audio driver. As you can see, it hasn't been updated in years and will not build correctly with modern kernels. Worse, it will still try and install and break your sound (as in the thread you linked).

When people want to update their audio driver, I point them here:
[https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

Hi, there i also use Mi notebook pro and have the same problem on ubuntu 16.04.3 LTS.

Tried upgrading alsa driver, but that page seems only have the version for ubuntu 16.04.1
Anyway i give it a try on xenial LTS version and it give me error: 

```
Error!  The dkms.conf for this module includes a BUILD_EXCLUSIVE directive which
does not match this kernel/arch.  This indicates that it should not be built.
```

I guess ubuntu 16.04.1 using older kernel version.
So should i lower my kernel version and re-update alsa driver using that?

Here is my alsa info:
[http://www.alsa-project.org/db/?f=ebddaeed84a4cc518646e639432eae4ffcf06938](http://www.alsa-project.org/db/?f=ebddaeed84a4cc518646e639432eae4ffcf06938)

---

### Post by Yellow Pasque on 2018-01-09
Try the 17.04/zesty package. It matches BUILD_EXCLUSIVE with correct 4.10.x kernel version.

---

### Post by synoday on 2018-01-09
Cool, just tried it and now both the speakers and microphone works well.

Thanks!

---

