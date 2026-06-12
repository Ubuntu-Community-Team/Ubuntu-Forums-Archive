---
title: "Great performance and ? about hibernation"
date: 2008-11-29
forum: General Help
---

### Post by tekwarren on 2008-11-29
First I have to say I was nervous about the performance a wubi install might lack but I was wrong! Ubuntu is simply flying for me. Maybe its due to 4GB of ram and x64 but I see almost no hard disk seek times...granted I haven't done a lot yet but still...props to the devs on this install option.

Second I know that wubi doesn't work with hibernation unless you do some things with a dedicated partition. Is it just the /swap that has to be "real" for hibernation to work? Would it be possible to run wubi with a swap pointed to flash drive for increased performance and possible hibernation functionality or is there more to it than that?

Thanks guys!


P.S. I know I said performance was great and then mentioned using flash for added performance...not trying to contradict myself but maybe in some cases it would help people having performance issues?

---

### Post by ago on 2008-12-01
> **tekwarren said:**
> Is it just the /swap that has to be "real" for hibernation to work?
yes, provided there are no other hardware incompatibilities

> Would it be possible to run wubi with a swap pointed to flash drive for increased performance and possible hibernation functionality or is there more to it than that?
Total number of writes on flash devices are limited not sure if you want to do that, but you can certainly try it.

---

### Post by tekwarren on 2008-12-01
as cheap as flash drives are I don't think it would to much of an issue, at least not for me. I would like to try this but haven't the slightest clue how to "move" or create and then "point" ubuntu to a flash drive swap. Any pointers or instructions? Also how big of a swap would be needed? The laptop I'm running on has 4gb of physical ram if that makes a difference.

---

### Post by ago on 2008-12-02
normally you just run mkswap on a partition (careful it will reformat it) and add that partition to /etc/fstab

---

### Post by tekwarren on 2008-12-02
Thanks that should be enough info to point me in the right direction, I'll give it a try and report back.

---

