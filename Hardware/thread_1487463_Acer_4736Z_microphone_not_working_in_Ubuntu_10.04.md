---
title: "Acer 4736Z microphone not working in Ubuntu 10.04"
date: 2010-05-19
forum: Hardware
---

### Post by butoyzki on 2010-05-19
hi, i am using an acer aspire 4736Z laptop and i can't seem to make the   mic work. All I'm getting when I record a message is static. It doesn't  work with  Skype too because I tried to call Test/Echo. apart from  that, everything else is ok, the sounds, etc.. do you know of any   configuration which might be able to help me out?

here are some details i got from my laptop:

```

cat /proc/asound/card0/codec#* | grep Codec

Codec: Realtek ALC888
Codec: LSI ID 1040
Codec: Intel G45 DEVCTG

``````

aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


```i did try to configure it using

```

sudo gedit /etc/modprobe.d/alsa-base

```and added
```

options snd-hda-intel model=acer
```but it didn't help me at all.  please help!

---

### Post by butoyzki on 2010-05-20
anyone, please help?!

---

### Post by noletolucas on 2010-05-29
same problem here.

i tried installing and compiling the ALSA module but now i've got another problem: my speakers doesn't mute when i plug the headphones in.

---

### Post by lidex on 2010-05-30
Does it work with sound-recorder? 
Try gnome-alsamixer.
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

Then use pulseaudio volume control (pavucontrol) to select your mic in 'Input Devices' tab.

BTW, the correct syntax for editing alsa-base:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```

---

### Post by abhishekgupta92 on 2010-09-16
I am suffering from the same problem. I also tried to install the gnome-alsamixer and alsamixer and adjust the volume settings, but this didn't help. I am using the Acer 4763 z laptop.

```

abhishek@trojan-horse:~$ gksudo gedit /etc/modprobe.d/alsa-base.conf
abhishek@trojan-horse:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC888
Codec: LSI ID 1040
Codec: Intel G45 DEVCTG

```

```

abhishek@trojan-horse:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Please help. Thanks in advance for helping.

---

### Post by abhishekgupta92 on 2010-09-16
Here are attached some of the inputs that illustrate my settings of the microphone.

[IMG]http://abhi7.com/temp/Screenshot.png[/IMG]

[IMG]http://abhi7.com/temp/Screenshot-1.png[/IMG]
[IMG]http://abhi7.com/temp/Screenshot-2.png[/IMG]
[IMG]http://abhi7.com/temp/Screenshot-3.png[/IMG]

---

