---
title: "Laptop - Wrong audio controls, cannot adjust volume"
date: 2007-05-04
forum: Hardware &amp; Laptops
---

### Post by lkz on 2007-05-04
I have a problem on my laptop - Zepto 6014W

The controls for audio in Gnome are mapped incorrectly. The only way I can get sound out of my laptop speakers is by turning on Headphone, which is fine. However there is no volume control for Headphone, so it's either loud or no sound.

I searched the web for answers and it only seems to be possible to change the settings with alsaconf, which is not included in alsa-utils package in Ubuntu.

So I hope someone who is a little more experienced with custom alsa configurations can point me in the right direction.

Thanks.

My audio-device from lspci

```

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

```

---

### Post by spier on 2007-05-04
Just a thought: check  what is setted in your speaker preferences and/or Volume control (right click a speaker icon, somewhere in a panel > Preferences | Open Volume Control)

---

### Post by lkz on 2007-05-05
> **spier said:**
> Just a thought: check  what is setted in your speaker preferences and/or Volume control (right click a speaker icon, somewhere in a panel > Preferences | Open Volume Control)

I have already tried this and couple of other things. The problem with the headphone is, that there is no volume control, just a checkbox, on/off.

---

### Post by aot2002 on 2007-05-05
sounds like your using oss driver and not the right driver alsa are you sure your using alsa driver?

what program are you using for playing music?

---

### Post by aot2002 on 2007-05-05
[https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/93859](https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/93859)

---

### Post by mattigras on 2007-05-20
I have an Acer Aspire 5570-4421. It has the Intel ICH7 sound (using alsa driver hda-intel). After about a month with no sound in Feisty on my new laptop I finally got it to work 10 minutes ago following this 

[http://ubuntuforums.org/showthread.php?t=305712]("http://ubuntuforums.org/showthread.php?t=305712")

  At first the sound would only come out of my headphones and not the speakers, but i was fooling around with the mixer and my speakers started working once i unmuted and turned up the volume of the "SURROUND" channel. Now i leave the surround channel turned up all the way and the PCM channel controls the headphones and the speakers.

As far as i can tell there is no way to automatically mute the speakers when headphones are plugged in, but i guess you can just mute the surround channel whenever you use headphones.  let me know if it works

---

### Post by morphodone on 2007-05-28
Thanks for info on the "Surround" channel  :D

---

