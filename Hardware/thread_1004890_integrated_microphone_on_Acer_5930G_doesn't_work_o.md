---
title: "integrated microphone on Acer 5930G doesn't work on UBUNTU 8.10"
date: 2008-12-07
forum: Hardware
---

### Post by bubu7 on 2008-12-07
Hallo!I'm using ubuntu 8.10 since a few time and this is my first message.
Microphone in my ACER 5930G doesn't work; I've tried with many application (Skype,Amsn,Ekiga) but nothing. I guess a problem with Alsa driver; I've looked for a long but i don't find solution.
External microphone works good, but i would like using internal microphone ;)
I'll be very happy if someone can help me.

Bye!

---

### Post by thoken on 2008-12-27
I got the same problem, anyone got any ideas or solutions?

---

### Post by superstas on 2009-03-24
Same problem on Fedora core 10 and earlier on ubuntu 8.04, 8.10 and kubuntu 8.10
](*,)

-----------
actualy wait i got it working i followed this instructions from [here]("https://help.ubuntu.com/community/HdaIntelSoundHowto") to install alsa again with the 
> cd alsa-driver*
sudo ./configure --with-cards=**hda-intel** --with-kernel=/usr/src/linux-headers-$(uname -r)
sudo make
sudo make install
then after install in console

alsamixer -Dhw
in playback:
mic 70%
mic boost 33%
capture:
mic boost 33%
capture 23%
capture1 0%
input source front mic
input source1 mic

then went to system->preferences->hardware->sound
and audio conferencing pick: 
sound capture: HDA Intel ACL888 Analog (ALSA)
and fired up sound recorder and finaly first time after 7 months i could hear my voice recorded :)))))

btw if you want to have mic in skype in option->sound devices->sound in choose HDA Intel (hw:Intel,0)

also F.... yeah it finaly works! :)

---

### Post by markbuntu on 2009-03-24
Most likely you need to add an option to the /etc/modprobe.d/alsa-base file for the snd-hda-intel driver. There is more on that here:

[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

There is an option listed for the 5920g so you might want to try that first before trying the other acer options. There are also links at the bottom to other threads that have listings by chip type that may be helpful.

---

### Post by dora1980 on 2010-09-07
Our integrated microphone on acer aspire 5532 doesn't work....how can we resolve this problem?

---

