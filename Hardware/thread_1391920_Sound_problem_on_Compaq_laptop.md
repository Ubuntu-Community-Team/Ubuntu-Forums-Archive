---
title: "Sound problem on Compaq laptop"
date: 2010-01-27
forum: Hardware
---

### Post by charlescarroll1 on 2010-01-27
I bought a new 64bit Compaq Presario CQ60 notebook about a month ago and installed Ubuntu 9.10. One of the problems I am having is that when I plug in my external speakers or headphones into the sound output, I still get sound coming from the laptops internal speakers. I tried playing around with the sound preferences a little bit, but still having the problem.

Does anybody have any suggestions?

---

### Post by mörgæs on 2010-01-28
This seems to be an old bug. Does this describe your problem?

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/129907](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/129907)

Post number 9 suggests a fix.

---

### Post by jjjjeremy on 2010-02-13
It didn't work for me. I have the same laptop, same problem.

Just to keep people from jumping to the above link, this is what I did:

Edit the file /etc/modprobe.d/alsa-base and add "options snd-hda-intel model=laptop" to a new line

---

### Post by charlescarroll1 on 2010-11-24
I updated to 10.10 and the issue with the audio jack seems to have corrected itself.

---

### Post by mörgæs on 2010-11-24
Good, please mark the thread 'solved'.

---

### Post by charlescarroll1 on 2010-11-24
In Ubuntu 10.4 LTS, it isn't solved...:-|

---

