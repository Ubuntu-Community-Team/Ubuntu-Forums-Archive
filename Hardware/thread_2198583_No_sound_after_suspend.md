---
title: "No sound after suspend"
date: 2014-01-09
forum: Hardware
---

### Post by danep on 2014-01-09
I'm running a completely fresh install of Ubuntu 13.10 Saucy. Audio out works fine when I first boot, but after it suspends and wakes up again, I get no more audio. There's no errors or changes in configuration that would seem to indicate a problem, there's just simply no more sound. If I open sound settings, and choose "Test sound" for analog output, there's no sound.

It takes a cold boot to fix this- simply restarting doesn't even help. 

It's not a problem on Windows, so I'm suspecting it's an incompatibility between my motherboard and Ubuntu. My motherboard is a Gigabyte G1 Sniper M3 (fairly common I think). I'm just using the built-in analog output.

Anyone have tips for troubleshooting?

---

### Post by Toz on 2014-01-09
Are there any error messages in your **/var/log/pm-suspend.log** or **/var/log/syslog** files around the time of suspend? Perhaps pertaining to your sound card?

After resume, does:
```
sudo alsa force-reload
```
...bring the sound back?

---

### Post by danep on 2014-01-23
Sorry for the delayed response, but this seems to be a Heisenbug. I wasn't able to recreate it, and it didn't occur for a week, but now it's back.

Reloading alsa had no effect. There don't seem to be any audio-related errors in the logs.

I'm becoming skeptical that it's related to suspend, since I can't seem to trigger it by manually suspending. I just know that it happens after the machine has been up for a while (which usually results in it suspending).

It seems like this must be a very low level bug if it persists through a reboot, but not a cold boot. Would that symptom narrow down what could be causing it?

---

