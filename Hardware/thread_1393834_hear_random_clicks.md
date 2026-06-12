---
title: "hear random clicks"
date: 2010-01-29
forum: Hardware
---

### Post by marbertone on 2010-01-29
Hello,
I have Ubuntu Karmic on a Sony Vaio. It goes almost perfectly, apart that I can hear random "click" sounds coming from speakers. The sound is the same as when in windows you mute and then de-mute speakers. Exactly the same. It's as if Ubuntu turns off speakers and then on again randomly. Do you know some tricks to get rid of them?
Thank you!
Mario Alberto :popcorn:

---

### Post by marbertone on 2010-03-04
Hi guys!
By hanging around on ubuntuforums I found a very good thread which solved this issue (random 'pops', not 'clicks' :) ) : you have to edit this file, which is ALSA config file:

```

gksudo gedit /etc/modprobe.d/alsa-base.conf

```

and put the "power saving" option down to 0! It was exactly this, an automatic off for the speakers.

See you guys!
Mario Alberto :popcorn:

---

### Post by stuartziane on 2010-04-04
> **marbertone said:**
> Hi guys!
By hanging around on ubuntuforums I found a very good thread which solved this issue (random 'pops', not 'clicks' :) ) : you have to edit this file, which is ALSA config file:

```

gksudo gedit /etc/modprobe.d/alsa-base.conf

```and put the "power saving" option down to 0! It was exactly this, an automatic off for the speakers.

See you guys!
Mario Alberto :popcorn:
EXCELLENT!!  This solves the issue!  Thanks!

---

### Post by Agent ME on 2010-04-04
Awesome, I was having the same issue whenever I had headphones plugged in and no other programs making sound!

---

