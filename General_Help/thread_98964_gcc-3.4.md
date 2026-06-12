---
title: "gcc-3.4?"
date: 2005-12-04
forum: General Help
---

### Post by [M] at on 2005-12-04
I'm sorry if this is a stupid or redundant question, but I'm such a n00b with linux that I don't even know how to properly search for the answers I'm looking for 8-[ 

I'm trying to compile the drivers for my RT2500-based wireless card and I'm running into trouble.  When I first ran make I was given the "command not found" problem.  Easy enough, it wasn't installed so I grabbed it from synaptic.  Now when I run make, it gets caught on trying to gcc-3.4 and won't compile the source.  I opened up Synaptic again, assuming it was the same issue, but I couldn't find gcc 3.4.  There was gcc, gcc-3.3, and gcc-4.0.  Does anyone know if I can somehow configure make (can make be configured?) to use a different version of gcc, or if there's another way to get the gcc-3.4 package?  I tried running

```

sudo apt-get install gcc-3.4

```

but it just told me package not found.  Remember, I don't have internet on my linux install because it's my wireless card that isn't working, so if there's a solution other than adding different apt-sources that'd be preferred.

Thanks very much and sorry if this question is a time-waster.

---

### Post by Lambert on 2005-12-04
Post your /etc/apt/sources.list here

gcc-3.4 is in the repositories, not sure why you don't see it.

also rt2500 driver is in breezy so you shouldn't have to compile. But there are some newer chipsets that aren't supported. Look here.

[https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/](https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/)

---

### Post by [M] at on 2005-12-04
[QUOTE=Lambert]Post your /etc/apt/sources.list here

gcc-3.4 is in the repositories, not sure why you don't see it.

also rt2500 driver is in breezy so you shouldn't have to compile. But there are some newer chipsets that aren't supported. Look here.

[https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/](https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/)[/QUOTE]

Oh, I didn't realize it was supported now.  That makes things way easier!  Thanks :cool:

---

