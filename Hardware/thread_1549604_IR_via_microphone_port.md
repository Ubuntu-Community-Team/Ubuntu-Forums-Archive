---
title: "IR via microphone port"
date: 2010-08-10
forum: Hardware
---

### Post by JebusWankel on 2010-08-10
I found an IR transceiver that came bundled with a cable set-top box. It looks like a pretty simple piece of kit, just a little IR sensor wired to a 3.5mm 1/8" headphone jack. I was wondering if I could use this to set up a remote with LIRC if I just plug it into my microphone jack? I did some rudimentary tests and with maximum amplification it can pick up a signal from a decent distance.

---

### Post by Fafler on 2010-08-10
I only think it works with the set-top box. Some tuner cards use the same jack for IR receivers, but i don't think it works with the microphone input. I think it's a serial TTL like connection, GND, 5v and data out. But the lirc homepage should have some data on it.

---

### Post by JebusWankel on 2010-08-10
Thanks, LIRC.org is quite helpful. I should have been googling for lirc soundcard input and homebrew lirc. Basically it's the alsa audio ir driver.

It's too late tonight, but tomorrow I'll investigate these links and determine if I'm going to do some soldering.

[http://www.lirc.org/html/audio-alsa.html](http://www.lirc.org/html/audio-alsa.html)
[http://ubuntuforums.org/showthread.php?t=477958](http://ubuntuforums.org/showthread.php?t=477958)

---

