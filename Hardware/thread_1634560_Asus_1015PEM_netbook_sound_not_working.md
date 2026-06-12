---
title: "Asus 1015PEM netbook sound not working"
date: 2010-11-30
forum: Hardware
---

### Post by CTenorman on 2010-11-30
Hi,

I'm unable to get sound working on my asus 1015 pem netbook. I tried following these instructions from the Ubuntu Wiki:

sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
 sudo apt-get update && sudo apt-get dist-upgrade
 sudo apt-get install linux-alsa-driver-modules-$(uname -r)

However this does not seem to have it working, despite all the steps working. Does anyone have any ideas on what I can do?

Thanks!

---

### Post by khamami on 2010-11-30
just install alsamixer GUI. you can use synaptic to find it. then unmute your speaker

---

### Post by CTenorman on 2010-11-30
Unfortunately the sound card is not showing up in alsamixer or the default gui for sound configuration. Any idea how I can activate it?

---

### Post by CTenorman on 2010-12-01
Actually, don't worry about it. After loading windows on the machine and loading the right drivers it seems the sound card is pooched. Ubuntu is not to blame! Thanks for your help though!

---

### Post by fryx01 on 2011-01-23
> **CTenorman said:**
> Actually, don't worry about it. After loading windows on the machine and loading the right drivers it seems the sound card is pooched. Ubuntu is not to blame! Thanks for your help though!

how did you do that actually?
i don't quite understand what you're saying
im also an asus 1015pem user, and im having the same sound  problem. but i have failed to find and answer.

---

