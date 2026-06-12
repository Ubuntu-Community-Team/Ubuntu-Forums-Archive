---
title: "BCM 4318 (Gateway Laptop) help.  Noob"
date: 2011-08-27
forum: Hardware
---

### Post by soonercntry on 2011-08-27
I'm only hours into UBUNTU.  I tried it 4+ years ago and bailed quickly. I'm determined not to duplicate that effort this time.


I have a Gateway Laptop with the BCM 4318 wireless card that i cant seem to get working properly.

I read a few articles prior to trying to get my wireless going.  What i took away from it is that i needed to install the following via Synaptic:

bcmwl-kernel-source
firmware-b43-installer


I don't know what to do from there.  Any help is appreciated.

---

### Post by soonercntry on 2011-08-27
update...


Upon further reading, I tried to go into the system settings and enable the BCM driver that I downloaded.

However, the driver is not being recognized at all.  It doesn't even show up in the "Additional Drivers" list (Nothing does for that matter).

I'm still stumped.  :confused:

---

### Post by foresthill on 2011-08-28
I don't think you can install the driver through synaptic and have it work. The way I did it was using the terminal.

This is the guide I used. Follow the guide for the version of Ubuntu you are using (you didn't tell us which). Kind of advanced, if you're not used to the terminal, but it worked for me:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Sounds like since you already installed the two files from Synaptic, you might be able to enter the two commands listed and be good to go. 

In any event, don't give up and keep trying it'll eventually work.

---

