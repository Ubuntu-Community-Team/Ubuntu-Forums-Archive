---
title: "Microsoft LifeChat LX-3000 - No Sound"
date: 2008-07-15
forum: General Help
---

### Post by AH JohnJ on 2008-07-15
Hello,

Earlier today I decided to uninstall Windows XP to try out Ubuntu. I have already done this once before, but could not figure out how to make my sound work, so gave up after a few hours. After installing Ubuntu for the second time, I've made no further progress on getting my sound to work with my headset (Microsoft LifeChat LX-3000).

I searched Google a few minutes ago and found a tutorial on these forums (how to fix your sound), but I'm not fully understanding it. The tutorial I read gave me a link to this ALSA (I think that is the name) website and told me to choose my manufacturer/vendor from a drop-down list, but from what I saw, it was just a folder uploaded in the root directory of the site; it was no help.

Could someone please help me out here?

Thanks!

---

### Post by FSHero on 2009-03-19
AH JohnJ:

I am using Kubuntu (KDE3) hardy (8.04) amd64. I plugged these headphones in and they just seemed to work! In KMix, the sound volumes controller, it appears as:
Microsoft LiveChat LX-3000.

There are a few oddities in the 60 seconds I've played with it. I used Amarok to listen to music in it, but if I pull the headphones's USB connection out then plug it back in again, there'll be no sound. I have to restart Amarok. (Also, must restart KMix to control the volume.)

To record sound in Audacity, I had to use the alsa-oss wrapper:
```
aoss audacity 
```

Then recording seemed to work fine.

Also, if I use the headphones, no sound seems to come out of my speakers.

---

