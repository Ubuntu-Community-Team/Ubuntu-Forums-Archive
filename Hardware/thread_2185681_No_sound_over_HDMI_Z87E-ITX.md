---
title: "No sound over HDMI Z87E-ITX"
date: 2013-11-03
forum: Hardware
---

### Post by PDiddlyDoodlyDo on 2013-11-03
I've recently built a new computer and I'm having some trouble with getting it to work. This post is about the HDMI output. Can anyone help?


Sorry if this is a hardware problem, and not a Ubuntu problem. I've googled a lot, and couldn't find anything that would narrow it down. Also, I've had a couple of really great responses from this community in the past, so I thought it would be a good start.


PROBLEM: Connecting my new build to my TV using HDMI will show a picture, but not produce any sound


Here's my setup:


Motherboard: AS ROCK Z87E-ITX
Processor: i7-4765T
RAM: 2 x 8GB Kingston 1600MHz DDR3
HDD: 30GB mSATA SSD + 5 x 2TB 3.5" HDD
Tuner: TBS6824
Case: HFX PowerNAS
TV: Samsung UE32D5000


I've tried installing Ubuntu 12.04.3 (64bit), and then updating via 'sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade'. Just to test the sound, I've tried playing iplayer, with no joy.


When using the DVI-I output together with one of the five HD audio jacks, I can get a picture and sound, but I was expecting to get all of that digitally using just a HDMI cable.


Any ideas why this isn't working?

---

### Post by Yellow Pasque on 2013-11-03
I'm not sure what version of kernel is needed for Haswell HDMI audio support, but should try the latest driver: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by PDiddlyDoodlyDo on 2013-11-08
Hi Temujin,

thanks for the reply. I've just tried the link you sent... Looks like a set of instructions to help diagnose the problem.

I ran both commands, and the results have been stored at [http://www.alsa-project.org/db/?f=04d4d8e382a1611aa54bcebf91316e867293ff37](http://www.alsa-project.org/db/?f=04d4d8e382a1611aa54bcebf91316e867293ff37)

Is that what you meant?

---

### Post by Yellow Pasque on 2013-11-08
Sorry, it was a copy/paste error on my part (though that information is definitely good to have). This was the link I was going for:
[https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

---

