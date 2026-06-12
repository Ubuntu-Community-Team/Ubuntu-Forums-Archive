---
title: "Does Linux support features such as fingerprinting"
date: 2007-07-04
forum: Hardware &amp; Laptops
---

### Post by nite owl on 2007-07-04
Hi I am specifically looking to buy a laptop to run Linux on but am concerned about whether to bother getting something like an asus a8sc or an thinkpad T61 or R61 because the T61 has so many features like fingerprint reader, active protection for the HD, this new technology that improves wireless and plus all these little features like a Santa Rosa(Centrino up/Pro) chipset. Would I be able to get all these working in Ubuntu 7.04 or would I be giving up some of the features?? Even the little special buttons and software..

---

### Post by egonkasper on 2007-07-04
Fingerprint readers are bad, they make someone who is stealing your laptop want to cut off your finger so they can log in!  Ok, I know this won't usually happen, but I have read of stories where it has been done.

/Couldn't resist.

---

### Post by nite owl on 2007-07-04
> **egonkasper said:**
> Fingerprint readers are bad, they make someone who is stealing your laptop want to cut off your finger so they can log in!  Ok, I know this won't usually happen, but I have read of stories where it has been done.

/Couldn't resist.

lol you know I thought of that and believe me the day I become a spy I will be using password protection :)

---

### Post by odinb on 2007-07-05
Well, cutting off someones finger will not work on the fingerprint scanners on new computers, since it is not reading the fingerprint....

It is actually reading electrical resistance, kinda like CAT-scanning your finger, so cutting it off will give an incorrect reading.

---

### Post by sr20ve on 2007-07-05
> **odinb said:**
> Well, cutting off someones finger will not work on the fingerprint scanners on new computers, since it is not reading the fingerprint....

It is actually reading electrical resistance, kinda like CAT-scanning your finger, so cutting it off will give an incorrect reading.

Well there's only one way to find out.

---

### Post by J-Red on 2007-07-05
Anyways, about your question, I bellieve my laptop has the Santa Rosa chipset in it, and at first it didn't work with Ubuntu. I had to edit the xorg files and it took me a couple days to get it working properly with Ubuntu. I finally did, but now the optical drive seems to be invisible to Ubuntu. I installed with the built in drive, but i cannot seem to get the built in drive to read any CDs or appear anywhere. About the finger print, its really not worth it. I don't know if it works or not, my laptop seems to recognize the fingerprint reader, but its not worth it to use it.

---

### Post by ciphermonk on 2007-07-06
To answer your question: Yes. The fingerprint reader does work under Linux and it's really easy to setup. I'm not sure if there's a thinkfinger package for Ubuntu, but if there is, install it and then run 
tf-tool --add-user <username> to add your user profile. You'll have to make a change to your pam config for login but it's very easy. The whole process takes all of 2 minutes. It's convenient to be able to just swipe you're finger for the initial login and when running privileged commands via sudo.

---

