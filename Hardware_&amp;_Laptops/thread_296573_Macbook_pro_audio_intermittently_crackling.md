---
title: "Macbook pro audio intermittently crackling"
date: 2006-11-09
forum: Hardware &amp; Laptops
---

### Post by rupy on 2006-11-09
Hey Guys,

I have been running (k)ubuntu on my macbook for almost 6 months now and one of my biggest annoyances is the sound on the left channel seems to crackle. Its not the hardware because if I plug in headphones the left chan still crackles and hisses slightly.

It is really weird because its hit and miss, once the audio crackling is there though it stays until I reboot, at which point when kubuntu starts up I either get the crackle or I dont.

Any ideas?

---

### Post by rupy on 2006-11-15
Bump... Anyone at all?

---

### Post by Yfrwlf on 2007-03-12
> **rupy said:**
> Bump... Anyone at all?

I only have problems with sound during 3D apps for some reason.  Maybe try muting some of the channels, or playing with the volumes to make sure that's not the issue either.  Perhaps try out upgrading to Feisty even though it's still alpha the newer drivers might fix it.  If it's only on one channel, I'm no expert in Linux, but it still possibly could be the audio hardware?  Does it do it in any other OS? :P  Sorry I can't be of more help.

---

### Post by Jason DeRose on 2007-03-14
I have the same problem on a Core Duo (not 2) MacBook, although it isn't intermittent.  There is constant crackling/static in the left channel.

I recently switched to Feisty, but the problem is still present.  I'm single booting at the moment, but in the next few days I'm going to reinstall OS X to determine whether it is a driver bug or a hardware problem.

---

### Post by Yfrwlf on 2007-03-16
> **Jason DeRose said:**
> I have the same problem on a Core Duo (not 2) MacBook, although it isn't intermittent.  There is constant crackling/static in the left channel.

I recently switched to Feisty, but the problem is still present.  I'm single booting at the moment, but in the next few days I'm going to reinstall OS X to determine whether it is a driver bug or a hardware problem.

Good idea, usually for me crackling has been because the volume is too loud, but I know that the Macbooks seem to also have poor audio driver support for them for whatever reason.  Also ATI has pretty sucky support too, I wish ATI would get off their butts and be more like Nvidia as far as driver support.  If it weren't for the ATI graphics and the poor audio support, I think buying a Macbook for Linux would be a possibility.

Did you try the sound test as well as playing music with an audio player and such?  How about changing to a different audio driver in the sound settings?  Maybe if a different driver works it might work better?

---

### Post by Jason DeRose on 2007-03-18
I setup a dual boot: this problem is not present under OS X, so it's not a hardware problem.

There is a bug report about this here: [https://launchpad.net/bugs/75906](https://launchpad.net/bugs/75906)

The MacBook (not Pro) uses an Intel graphics chipset, for which Intel has not only released full specifications, but also released GPL'd driver code that has been integrated into x.org.

---

### Post by Jason DeRose on 2007-03-20
I just posted a work-around that seems to work consistently at least on my MacBook Core Duo:

[https://launchpad.net/bugs/75906](https://launchpad.net/bugs/75906)

---

