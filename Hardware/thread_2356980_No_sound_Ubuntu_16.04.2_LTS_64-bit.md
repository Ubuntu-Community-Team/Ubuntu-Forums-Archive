---
title: "No sound? Ubuntu 16.04.2 LTS 64-bit"
date: 2017-03-28
forum: Hardware
---

### Post by blkmajik on 2017-03-28
I did a fresh install today of gnome ubuntu, but I'm not getting any sound. Nothing is muted. I've used live usb of other distros with the same problems. Windows 10 plays sound fine though. Any ideas? Some little info:

```

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889 Digital [ALC889 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

sudo lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller

```

---

### Post by RobGoss on 2017-03-28
Hello and welcome, Click on the sound icon at the top right hand side of your desktop, Open up your sounds settings do you see your sound device listed in the output tab?

Another suggestion would be try using **Alsamixer** sometimes the sound level is to low were it cannot be heard, use this link [https://wiki.ubuntu.com/Audio/Alsamixer](https://wiki.ubuntu.com/Audio/Alsamixer)

---

### Post by blkmajik on 2017-03-28
I dont believe my device is listed. This is what I have:

[IMG]http://i64.tinypic.com/f9mgia.png[/IMG]

---

### Post by blkmajik on 2017-03-28
> **RobGoss said:**
> Hello and welcome, Click on the sound icon at the top right hand side of your desktop, Open up your sounds settings do you see your sound device listed in the output tab?

Another suggestion would be try using **Alsamixer** sometimes the sound level is to low were it cannot be heard, use this link [https://wiki.ubuntu.com/Audio/Alsamixer](https://wiki.ubuntu.com/Audio/Alsamixer)



I also tried alsamixer by unmuting anything and testing the sound, but still nothing.

---

### Post by RobGoss on 2017-03-28
Did you try clicking on the top option in that screen shot to see if that will enable your sound device?

---

### Post by blkmajik on 2017-03-28
> **RobGoss said:**
> Did you try clicking on the top option in that screen shot to see if that will enable your sound device?

Yeah, I also tried that option but still no sound. Not sure what's going on

---

### Post by RobGoss on 2017-03-29
When you run the live installer did you check to see if the sounds was working?

After looking at your first post it looks like the sound device is available but just to make sure

Try running the following command to see if your sounds card is listed, in some cases the system may not be detecting your device and may have to be installed manually 

```
 aplay -l 
```

---

### Post by blkmajik on 2017-03-29
> **RobGoss said:**
> When you run the live installer did you check to see if the sounds was working?

After looking at your first post it looks like the sound device is available but just to make sure

Try running the following command to see if your sounds card is listed, in some cases the system may not be detecting your device and may have to be installed manually 

```
 aplay -l 
```

Live installer didnt have sound either. Ive tried other live installers from other distros too

```
$  aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889 Digital [ALC889 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


```

---

### Post by RobGoss on 2017-03-29
Have you tried installing the additional **proprietary** drivers that's provided by Ubuntu? assuming you can connect to the internet

**Software & Updates**, **Additional drivers**, Then choose from the list that is provided

---

### Post by blkmajik on 2017-03-29
> **RobGoss said:**
> Have you tried installing the additional **proprietary** drivers that's provided by Ubuntu? assuming you can connect to the internet

**Software & Updates**, **Additional drivers**, Then choose from the list that is provided

This is what I have in that section:

[IMG]http://thumbsnap.com/i/NIgxztGR.png[/IMG]

---

### Post by Yellow Pasque on 2017-03-30
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by blkmajik on 2017-03-30
> **Temüjin said:**
> [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)


[http://www.alsa-project.org/db/?f=4f43bae06d109bb49a1039580ae1347649bd6675](http://www.alsa-project.org/db/?f=4f43bae06d109bb49a1039580ae1347649bd6675)

Uploaded

---

### Post by Yellow Pasque on 2017-03-30
I suggest filing a bug report on the launchpad and/or kernel bugzilla. It's possible your model needs a fix like: [https://github.com/raspberrypi/linux/commit/e427c2375646789ecd0ccaef1a1e41458559ab2d#diff-8e4f02d4cabdab00ba739107056d2b77R59](https://github.com/raspberrypi/linux/commit/e427c2375646789ecd0ccaef1a1e41458559ab2d#diff-8e4f02d4cabdab00ba739107056d2b77R59)

---

### Post by blkmajik on 2017-03-30
> **Temüjin said:**
> I suggest filing a bug report on the launchpad and/or kernel bugzilla. It's possible your model needs a fix like: [https://github.com/raspberrypi/linux/commit/e427c2375646789ecd0ccaef1a1e41458559ab2d#diff-8e4f02d4cabdab00ba739107056d2b77R59](https://github.com/raspberrypi/linux/commit/e427c2375646789ecd0ccaef1a1e41458559ab2d#diff-8e4f02d4cabdab00ba739107056d2b77R59)

How would I go about filing a bug to Bugzilla? New to this. Would I report it as hardware, then x86_64, kernel: 4.8.0-45-generic, and a summary? Do I need to add anything else? TIA!

---

### Post by Yellow Pasque on 2017-03-31
> **blkmajik said:**
> How would I go about filing a bug to Bugzilla?

Register an account and file a bug against Drivers -> Sound(ALSA). Provide your alsa info link and copy/paste the link I gave you and ask if your machine needs that fix.

---

### Post by geekhush on 2017-08-16
Any update guys? i have been having this problem for a long time now and every time i have to restart to get my sound back.

---

### Post by Yellow Pasque on 2017-08-16
> **geekhush said:**
> Any update guys? i have been having this problem for a long time now and every time i have to restart to get my sound back.

What makes you think your issue is related to this thread?

---

