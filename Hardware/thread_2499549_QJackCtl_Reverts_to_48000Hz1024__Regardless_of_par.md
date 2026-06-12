---
title: "QJackCtl Reverts to 48000Hz/1024  Regardless of parameters"
date: 2024-07-30
forum: Hardware
---

### Post by 2normee2 on 2024-07-30
Hello,

I recently upgraded from jammy jellyfish to noble nimbat 24.04 LTS with a fresh install 

Using a Mackie Onyx board connected via Firewire.  Everything was working great in jammy and was connecting with qjackctl 44.1K sample and 32 frames.. had very low latency and no x-runs

On new install it will only start the JACK server  @ 48K/1024  NO MATTER what setting I pass to it.  It will always revert to 48K/1024.  It works at that setting , however the latency at that frame rate is around 28ms when tracking in Adour.  Which makes it unusable.

I have tinkered for hours, searched on the forums, searched the web and cannot seem to come to a solution.

I have a feeling it has something to do with pipewire being the default in the newest ubuntu studio, but it is beyond my technical ability to know what it happening 

Any help would be greatly appreciated!!!


Cheers!!!

---

### Post by ajgreeny on 2024-07-31
I don't know ardour at all but I'm aware of pipewire difficulties in some situations which have been overcome by moving sound settings back to pulse. Give that a try to see if it works for you as well.

---

### Post by bobunderwood99 on 2024-07-31
QJackCtl cannot control pipewire-jack. 

You can set the sample rate and Quantum (buffer size) per session from a terminal using 

```
pw-metadata -n settings 0 clock.force-quantum  512
pw-metadata -n settings 0 clock.force-rate  48000
```
There are various GUIs available for this as well.

[URL="https://gitlab.freedesktop.org/pipewire/pipewire/-/wikis/home"]https://gitlab.freedesktop.org/pipewire/pipewire/-/wikis/home  

[/URL]You can also set Sample Rate and Quantum with Ubuntu Studio Audio Configuration (set them before starting Ardour).

[https://ubuntustudio.org/audio-configuration/](https://ubuntustudio.org/audio-configuration/)

Have you tried using Ardour's ALSA back-end?

---

### Post by 2normee2 on 2024-08-05
Followed the guide in the link and used Ubuntu Studio Audio Configuration to set.  

Works perfectly Now!! :P

I am now able to change the setting at will..  

Figured it would be something simple!  Just was not sure how it was handled in 24.04. Great information in the links 

Thank you @ bobunderwood99

---

### Post by bobunderwood99 on 2024-08-05
I'm glad it's working for you now.

Please mark the thread as solved.

---

