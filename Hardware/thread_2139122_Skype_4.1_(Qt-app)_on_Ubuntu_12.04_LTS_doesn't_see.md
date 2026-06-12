---
title: "Skype 4.1 (Qt-app) on Ubuntu 12.04 LTS doesn't see Sony Wireless Headset"
date: 2013-04-26
forum: Hardware
---

### Post by mrquesty on 2013-04-26
Hi Everyone,

I have Sony Wireless Headset (SWH), it works just fine in Chrome, Rhythmbox, etc: connected, turned on and everything works fine.

But Skype is a different world: it has it's own sound configuration, where it offers lots of options, where one can choose SWH.

The issue I'm facing now is the following: Skype sees SWH for mic, but not for speakers/ringing, therefore it was fine just a few days ago.

I tried to restart Skype, Ubuntu, apply the latest updates, restarts, configuration changes, nothing works in Skype, but just fine in other app's.

Pulse audio and alsamixer work fine, lsusb shows SWH, but Skype states it has many devices available, but not SWH...

Stuck with this for a while, hope anyone knows, what else to check/configure.

Thanks a lot in advance for any hints/solutions.

Best regards,
Vladimir.

---

### Post by mrquesty on 2013-04-26
Hi,

I have read this doc [http://www.alsa-project.org/main/index.php/Asoundrc](http://www.alsa-project.org/main/index.php/Asoundrc) and followed instructions, provided there: created /etc/asound.conf with default settings, installed PulseAudio Volume Control and deactivated all devices, but SWH; restarted Skype and, magic, Skype sees SWH now and works properly.

Hope, this would help other folks.

BR,
Vladimir.

---

