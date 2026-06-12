---
title: "Mint Lint 15"
date: 2013-07-05
forum: Hardware
---

### Post by gordie69 on 2013-07-05
Hey guys question for you I put Mint 15 on a friends Acer laptop not that old quad core 8 gigs of ram good laptop but anyways put mint 15 on it and I can't seem to get the web cam. I went to system settings and the tab input where it should wasn't there was what happened I never had a problem like this with my laptop it always picked up the web cam. I'm thinking on trying Ubuntu 13.04 for him and see if that picks it up

---

### Post by DeathByDenim on 2013-07-05
Odd. I've owned two Acer laptops so far and in both cases the webcam just worked. That was using Kubuntu though, but I'm sure it should work for Mint too.
Do you have an entry for /dev/video0 or similar?
Does "Cheese" pick it up? (That's a webcam program, which you can install from the repositories)
Does it show up when you type
```
lsusb
```
?
Are there any messages about the webcam when you type
```
dmesg
```
?

---

### Post by gordie69 on 2013-07-05
Ya I tried that so I was going to try Ubuntu 13.04 64 bit and hopefully it brings up the web cam I never had a problem with my laptop and mine is a couple years older and it picked up the web cam right away went to system settings and input tab and there it was.
So I'll keep you posted on what we decide to do

---

