---
title: "Alsa, trouble with shutdown and audio hw detection"
date: 2010-10-09
forum: Hardware
---

### Post by jeff.boyes on 2010-10-09
Hi,
alsa doesn't seem to like my notebook very much, since upgrading to Lucid.
Here are my symptoms
1) unable to shutdown or restart via gui. It goes to login screen instead. I can still use sudo shutdown now to shutdown tho.
2) when i use sudo shutdown now, when the OS finishes shutting down the computer doesn't power down, and I get some nasty psychedelic corruption all over my screen.
3) no audio hardware detected.

I can make all of these symptoms go away if i do:
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
and:
sudo apt-get install linux-sound-base alsa-base alsa-utils
after every boot.

if i ever forget to run those two commands, the above problems will come back on next boot.

I had it working properly on Karmic. So I'm sure it must be possible on Lucid.
Computer is an Acer Travelmate 8104. I installed Lucid via a live USB stick of Karmic, then immediately upgraded to Lucid.

Can anyone help me to get these problems to go away permanently?
thanks,
Jeff

---

### Post by jthirt on 2010-12-07
I have a very similar issue on a desktop running Maverick. It is a fresh install since I had to reinstall following a disk crash! :(

Looking into the logs I found a message that may be related: 

```
pulseaudio[1610]: alsa-mixer.c: Your kernel driver is broken: it reports a volume range from 0,00 dB to 0,00 dB which makes no sense.
```

This system worked fine before with Karmic and everything looks fine when running XP. I have not yet managed to convert my wife to ubuntu! ;)

I can't find anything searching for bugs in launchpad, but then it's not always easy to use the right keywords.

This is a pain.

---

