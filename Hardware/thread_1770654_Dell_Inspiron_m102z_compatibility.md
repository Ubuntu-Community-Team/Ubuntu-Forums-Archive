---
title: "Dell Inspiron m102z compatibility"
date: 2011-05-29
forum: Hardware
---

### Post by erlguta on 2011-05-29
Hi.
The new Dell Inspiron m102z looks great with the new amd fusion technology.
I open this post for the people who is planning to install ubuntu on it to check the hardware compatibility, like performance, suspend/hibernate, wifi, hdmi port, noise level, battery life, etc
Any feedback will be greatly appreciated.

---

### Post by ivannz on 2011-05-29
Got my m102z on the weekend. Not much info out there yet. Glad to have found your post.

---

### Post by ivannz on 2011-06-01
Loaded 11.04 64 bit last night

No issues so far.

---

### Post by azovat on 2011-06-02
I have problem getting both the internal and external microphone to work on ubuntu 11.04. Anybody has been so lucky so far?

---

### Post by erlguta on 2011-06-02
> **ivannz said:**
> Loaded 11.04 64 bit last night

No issues so far.

Ivannz, does suspend to RAM (and resume) works ok?
and hibernate?... for me are two important options.
And how is noise level and battery life?
Any revision from you will be very appreciated.
Thank you

---

### Post by azovat on 2011-06-07
I found the solution for microphone problem as per link below :

[http://ubuntuforums.org/showthread.php?t=1685384](http://ubuntuforums.org/showthread.php?t=1685384)

or 

sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)

---

