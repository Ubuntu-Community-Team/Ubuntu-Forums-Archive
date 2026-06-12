---
title: "No sound on Apple TV under Jaunty"
date: 2010-02-16
forum: Hardware
---

### Post by jpincheira on 2010-02-16
Hi guys. I've installed Jaunty using a minimal install on the Apple TV, but I'm getting no sound. 
In order to get the sound working I simple installed these packages:
```
sudo apt-get install linux-sound-base alsa-base alsa-utils
```
which would always work on the latest Ubuntu versions (Hardy and Intrepid).

I can confirm that the RCA audio output works flawlessly on minimal installs I made using Jaunty and Hardy, just by installing the software listing above.

My goal is to only get the RCA to work, I'm not worried about getting the HDMI audio to work yet. **[There's been some success stories on getting HDMI audio to work though.]("http://artem-astafyev.blogspot.com/2008/11/hdmi-audio-in-linux-running-on-apple-tv.html")**

The Apple TV sound card uses the snd-hda-intel module as a driver, and it has two outputs, RCA and HDMI. What I think is that the system is getting confused because of the two outputs, it tries to make the HDMI audio work or something, because when I run alsamixer it shows up only the HDMI audio controls:

[IMG]http://vidarara.com/images/alsamixer.jpg[/IMG]

Some of you might just say: "Why don't you just install Karmic on it." But I have to respond that it's been really tricky to boot it on the Apple TV using the ATV-Bootloader since this bootloader is not designed for GRUB 2. I tried to follow some success cases that I saw on the ATV-Bootloader mailing list, but there's no formal documentation on this matter. **[Here's more reference on this issue.]("http://www.mail-archive.com/atv-bootloader@googlegroups.com/msg00614.html")**

When I execute aplay -l to list the sound devices, this is the output I get:

```
user@AppleTV:~$ sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
user@AppleTV:~$ 

```


I ran the Alsa info script, and here's the output:
[http://www.alsa-project.org/db/?f=3fa0cc5e07b3f2d8b1f1b8059d8822c76345c09e]("http://www.alsa-project.org/db/?f=3fa0cc5e07b3f2d8b1f1b8059d8822c76345c09e")

It might be helpful for you to help me to show you the outputs *I get on Intrepid*, where the audio works flawlessly:
```
user@AppleTV:~$ sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC885 Analog [ALC885 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC885 Digital [ALC885 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
user@AppleTV:~$ 

```

```
user@AppleTV:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC889A
Codec: Silicon Image ID 1390
user@AppleTV:~$ 

```

I also compiled Alsa following all the instructions of this forum post: [Disabling graphics card's HDMI]("http://ubuntuforums.org/showthread.php?t=1274344") but go no results on getting audio to work.

Thank you guys.



jp

---

