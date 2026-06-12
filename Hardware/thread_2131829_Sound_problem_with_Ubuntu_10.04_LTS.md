---
title: "Sound problem with Ubuntu 10.04 LTS"
date: 2013-04-02
forum: Hardware
---

### Post by neilmaclennan on 2013-04-02
I am having a sound problem. I am running Ubuntu 10.04 LTS 32bit on a Gateway 4530GZ (updates installed no proprietary drivers though)

The sound seems to be off when I restart the computer. I have checked the Alsa settings and all "seems" to be well there. And all of the updates for the Audio are installed too. 

I have found that if I go to Sound Preferences -> Output -> and choose "Analog Output / Amplifier" and then switch it back to "Analog Output / No Amplifier" the sound works again.

The only software that I have removed were the default movie and music players as I use VLC instead. I don't know what to do other than attempt to create a script (my first script too by the way, am a total nub) that runs the above workaround at each startup. I would rather apply a fix properly rather than bandaid the solution together. Thanks for any help regarding this.

:p

---

### Post by mörgæs on 2013-04-03
As noone seems to have a better solution: I would try Xubuntu 12.04.2 in a fresh install. 10.04 is old and soon to run out of support anyway.

---

### Post by breezypt on 2013-04-03
Try going into /etc/modprobe.d/blacklist.conf in terminal. First you have to find the offending driver and try blacklisting it. First comment out what and why you are blacklisting it for future reference. Chances are that 2 drivers are conflicting with each other and the one that is winning on reboot is the wrong one. So blacklisting it very well may solve your problem.

---

