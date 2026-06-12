---
title: "Sound not working on Sony Vaio with 10.04"
date: 2010-06-19
forum: Hardware
---

### Post by unmole on 2010-06-19
There is no audio output from my laptop's internal speakers or attached headphones (Sound works in Windows 7). I've checked the basics but the all seem to be fine. lspci shows audio device as **ATI Technologies Inc RV710/730 **and cat /proc/asound/card0/codec#* | grep Codec shows **Realtek ALC269**. Any help would be appriciated.

---

### Post by ichramm on 2010-06-22
Hi, I had the same problem with the same hardware (at leats mi Realtek codec is the same than you).

I have a sony vaio VPC EA1S1E.

Installing the alsa driver from teh development repositories could fix half of the problem, it works with stereo headphones but the internal speakers are still not working (if you fix it let me know please).

If you want to install the alsa driver here is the required command line
sudo apt-add-repository ppa:ubuntu-audio-dev/ppa/ubuntu
sudo aptitude install linux-alsa-driver-modules-$(uname -r) linux-backports-modules-alsa-$(uname -r)-
reboot

Regards
   Juan

---

### Post by zombiezparadize on 2010-07-05
I have a Sony Vaio VPCE18FD and had the same problem as you mentioned. I was looking around for a solution when I stumbled upon this [known alsa bug]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/537448").
I used the workaround mentioned in comment #102 and said "Let there be Sound!" 
And there was sound!

---

### Post by lidex on 2010-07-05
> **unmole said:**
> There is no audio output from my laptop's internal speakers or attached headphones (Sound works in Windows 7). I've checked the basics but the all seem to be fine. lspci shows audio device as **ATI Technologies Inc RV710/730 **and cat /proc/asound/card0/codec#* | grep Codec shows **Realtek ALC269**. Any help would be appriciated.

Have you found a solution?

---

### Post by grigri on 2011-02-15
hey all i have a VAIO vpcEB33FX I am an ultra n00b but I have attempted all of the suggestions in this and some other threads.

when I run aplay - l I get[HTML]user:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
Subdevices: 1/1
Subdevice #0: subdevice #0[/HTML]

and when i run:cat /proc/asound/card0/codec#* | grep Codec
i get [HTML]
Codec: Realtek ALC269
Codec: Intel G45 DEVIBX[/HTML]

and now I am here. still no sound, but the wifi and all that works, any suggestions

---

### Post by lidex on 2011-02-16
> **grigri said:**
> hey all i have a VAIO vpcEB33FX I am an ultra n00b but I have attempted all of the suggestions in this and some other threads.

when I run aplay - l I get[HTML]user:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
Subdevices: 1/1
Subdevice #0: subdevice #0[/HTML]

and when i run:cat /proc/asound/card0/codec#* | grep Codec
i get [HTML]
Codec: Realtek ALC269
Codec: Intel G45 DEVIBX[/HTML]

and now I am here. still no sound, but the wifi and all that works, any suggestions

More info please. Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by Vignesh9 on 2011-02-16
I have a VAIO VPCEB14EN.  I have installed Ubuntu 10.04. I have come across many problems and hoping to find a solution here.

1.There is no sound coming from my laptop. 
2. The Sound and Brightness controls are not working, thus it's always on high brightness which hurts the eyes.
3. The wireless network connects for a while and then it goes offline. 
4. The graphics are low key, but I had updated the system and the graphics seem to be working now. 

Can anyone help me out.  I really love using Ubuntu and it's sad that I can't due to compatibility issues!

---

