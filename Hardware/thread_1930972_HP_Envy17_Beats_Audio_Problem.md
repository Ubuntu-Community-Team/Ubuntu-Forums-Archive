---
title: "HP Envy17 Beats Audio Problem"
date: 2012-02-24
forum: Hardware
---

### Post by dmanweb on 2012-02-24
I have an HP Envy17 with Beats Audio and installed Ubuntu 11.10 Desktop 32bit on the machine as soon as I got it. Everything has been awesome except for a *major* audio delay on boot and seemingly random other times. The sub woofer problem was easily fixed by adding

```
options snd-hda-intel model=ref
```

to the bottom of /etc/modprobe.d/alsa-base.conf also the sub *still plays sound when headphones are plugged-in. I've tried everything I can find including all of the options described [here]("http://ubuntuforums.org/showthread.php?t=1908225&highlight=beats+audio"). That is just an annoyance and not my real problem.

My real problem is that on boot, the audio takes about 4 minutes to work. The boot-up ubuntu sound starts on boot and then abruptly stops only to finish playing about 4 minutes later.

During the time that audio doesn't work, I can see a stream of messages in the syslog that all look like this.

```
kernel: [ 4489.032196] 3:1:1: cannot set freq 44100 to ep 0x1
```

At the end of that stream, there are two entries like this:

```
pulseaudio[15284]: [pulseaudio] alsa-mixer.c: Unable to load mixer: Invalid argument
```

After that, audio work find for a long while. There will be random times where audio stops working and sure enough, the syslog is getting a stream of the above errors.

---

### Post by dmanweb on 2012-02-24
Oh yeah, [here]("http://www.alsa-project.org/db/?f=cd45688c8591a814c922f2a91f4028498b7143d2") is my alsa info.

---

### Post by bramswenson on 2012-03-05
Hey there. I had similar issues with my new 2012 HP Envy 15 3040nr. It has the exact same sound card setup, as well as other features. My issues seemed to be worse than you have described as all of Gnome would become unresponsive while these errors were scrolling through syslog:

```
cannot set freq 44100 to ep 0x1
```

Finally I was ready to admit defeat and decided to blacklist the sounds card to at least have a working desktop without sounds. I added the following to /etc/modprobe.d/alsa-base.conf:

```
blacklist snd-hda-intel
```

After rebooting, to my surprise, those log messages remained and I was still left with an almost useless laptop, locking up on sound card issues. This made me think about the fact that in Windows there was also a usb sound card listed in the audio devices. So I decided to checkout

```
lsmod | grep snd
```

And sure enough, snd_usb_audio was loaded. So I added the following to /etc/modprobe.d/alsa-base.conf:

```
blacklist snd-usb-audio
```

And rebooted once again. Guess what, that's right, a fully responsive Gnome! Could it be, so I removed the blacklist for the intel sound card and instead added the following to /etc/modprobe.d/alsa-base.conf:

```
options snd-hda-intel model=auto
```

And after a final reboot, holy shnikeys Batman, sound and a super slick fast as fire Gnome! Guess what, I don't even like usb-audio, it tastes terrible.

Baller out.

---

### Post by dmanweb on 2012-03-07
Thanks for the response! the blacklist does indeed fix the errors and delay issue. Thing are responsive! The downside, it seems, is that the sub woofer no longer works, so listening to music doesn't sound great. It is better than waiting a while for the audio to start though. I'll use this solution until there is better support for the usb audio part of the beats audio system.

Thanks again!

---

### Post by dirktanyan on 2012-03-20
Thanks for the info. I've been struggling with sound on my Envy15 too. Sometimes it would work; sometimes it wouldn't. This seems to have fixed it!

---

### Post by Lancealot on 2012-05-15
Excellent fix, thank you!

---

