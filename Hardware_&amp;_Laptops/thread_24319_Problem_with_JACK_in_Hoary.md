---
title: "Problem with JACK in Hoary"
date: 2005-04-06
forum: Hardware &amp; Laptops
---

### Post by cyberloon on 2005-04-06
I'm trying to start jack under the current version of Hoary, but it stalls. My console looks like this when I try:

```
cyberloon@Istari:~ $ jackd -d alsa
jackd 0.99.0
Copyright 2001-2003 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

loading driver ..
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 48000Hz, period = 1024 frames, buffer = 2 periods
Couldn't open hw:0 for 32bit samples trying 24bit instead
Couldn't open hw:0 for 24bit samples trying 16bit instead


```

Then it just stops, very similar things happen when I try it with oss. I know that alsa and oss both work, because when I try using Hydrogen or XMMS it plays excellently.
I of course begin by running
```
sudo killall esd
```

---

### Post by 23meg on 2005-04-06
what audio device are you using and what arguments do you launch jack with?

---

### Post by cyberloon on 2005-04-07
I have tried starting it with hw:0 and hw:1, as you can see from the printout above I started it with just "-d alsa", you can also see there what assumptions it makes. e.g. hw:0, 32-bit, ...

---

### Post by 23meg on 2005-04-07
in other words, what soundcard are you using?

---

