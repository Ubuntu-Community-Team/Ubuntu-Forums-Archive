---
title: "No sound at startup"
date: 2016-11-02
forum: Hardware
---

### Post by davidlondonuk on 2016-11-02
Hi all,

I am using xubuntu 16.04 and have a problem with the sound not starting at boot. I can use 'sudo alsamixer' to un-mute headphones+LO and turn up the headphones+LO volume which restores the sound for some reason. Here is an image of how alsamixer looks after booting up:

[https://dl.dropboxusercontent.com/u/110067954/Screenshot_2016-11-01_21-27-51.v01.png](https://dl.dropboxusercontent.com/u/110067954/Screenshot_2016-11-01_21-27-51.v01.png)

How do I get Xubuntu to have the sound working at boot. My desktop system is a Dell Precision 380.

Thanks for any help.

---

### Post by ajgreeny on 2016-11-02
Have you checked in pulseaudio?

Go to the volume icon in the panel and from there to **Sound Settings** -> **Output Devices** tab which may help you to set things as you want.

---

### Post by davidlondonuk on 2016-11-12
Hi all,

My sound card is HDA Intel with the SigmaTel STAC 9200 chipset. 

I added a script to sessions/startup in xubuntu: 

```
sleep 10 && amixer -c 0 set Headphone+LO 90% unmute &
```

This script works at boot, the problem is if pulseaudio (alsa?) decides that Headphones+LO is inactive after a period of time, it mutes it and reduces volume to zero. 

Is there anyway around this? The strange thing is, I have virtually the same set-up on a Dell Latitude E6400 laptop but it doesn't have this problem.

Thanks for any help.

---

