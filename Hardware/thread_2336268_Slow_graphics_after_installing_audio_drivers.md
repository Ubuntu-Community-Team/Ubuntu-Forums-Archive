---
title: "Slow graphics after installing audio drivers"
date: 2016-09-06
forum: Hardware
---

### Post by macodo2 on 2016-09-06
Hey everyone,

I have a little problem with my Kubuntu Desktop machine. I'm using Kubuntu 14.04 x86 with the older KDE interface
because I couldn't get my graphics drivers working on 16.04 x64 and x86. Yes and I'm using fglrx-updates drivers for my old hd r5450 GPU.

The problem is I've had a little trouble getting sound from the HDMI port on my GPU so I followed an instruction on updating Audio Alsa DKMS drivers it this [link]("https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS?action=fullsearch&context=180&value=4.2+-+use+the+oem-audio-hda-daily-lts-wily-dkms+package+.deb&titlesearch=Titles"),I've used the this packege  _oem-audio-hda-daily-lts-wily-dkms _for my kernel 4.2.0-42-generic, After I rebooted my machine audio still didn't work but I resolved it later with KDE mixer by manually changing the output device of each application to HDMI. So the problem is when I tried to play a youtube video at 720p  it was very slow meaning there was a lot of latency in video and the sound didn't match the image. So I removed the package and rebooted again.

The graphics drivers are still not working before I installed that package I could have played 1080p and now it lags even if I play videos a 480p or 360p.
When I play games its even worse I think there could be some interference between those drivers. I would be much appreciative if someone helped me.

Thank you.

---

### Post by Yellow Pasque on 2016-09-06
I'd start here: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)
Also, a quick look at:
```
fglrxinfo
```

---

### Post by macodo2 on 2016-09-07
quick update... I have reinstalled Kubuntu because I was stressed out because it didn't seem to fix anything. I'd say its even worse,
do you have any idea why it might be so slow.

---

### Post by Yellow Pasque on 2016-09-07
Let's back up.
> I couldn't get my graphics drivers working on 16.04 
Did you even try to use the pre-installed open source radeon driver or did you just assume that you needed fglrx/Catalyst? If so, what went wrong with the open source driver?
The open source driver is better than fglrx in many ways, especially video playback.

---

### Post by macodo2 on 2016-09-08
Thank you for your reply. Yes I did try the open-source drivers on 16.04 they did work but there was still some latency in video playback.
I am using the open-source drivers now on 14.04 and they seem to work decent here. I dont know if you know anything about these things but
I'm kind of a student programmer I'm currently working with OpenGL and I'm interested in how the drivers work may be try to contribute in development.
I dont know much about drivers/modules but do you know where I can get some more info if you understand me if not then ok I will probably create a new thread.

---

### Post by Yellow Pasque on 2016-09-08
> Yes I did try the open-source drivers on 16.04 they did work but there was still some latency in video playback.

Did you try installing mesa-vdpau-drivers package and using a player that supports VDPAU (like mpv). THat's how I got the best results on my old RadeonHD 4550.

---

