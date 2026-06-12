---
title: "Dell M1730 - Need Help With Mic"
date: 2009-04-28
forum: Hardware
---

### Post by dethredic on 2009-04-28
So, I haven't been able to get my mic to work yet.

I was looking through [this]("http://ubuntuforums.org/showthread.php?t=563031") thread, and near the end people seemed to have some solutions, but I didn't understand them or they didn't work.

The best reply seemed to be this:

> 
internal microphone works great for me with alsa-driver-hg20080426 daily snapshot. just configured

./configure --with-cards=hda-intel
CC=gcc-4.1 make
sudo make install

remove any options snd-hda-intel from /etc/modprobe.d/alsa-base
reboot
select Digital Input Source [Digital Mic 1]
in Playback->Digital
also i've Input Source [Mic] in Capture

do not forget to install linux headers and other stuff
hope this will work for you too )))


I couldn't find that driver available to download on google, and I don't understand some of the steps.

I have everything unmuted etc in the volume manager. Any help would be appreciated.

---

