---
title: "USB microphone stops working after a few seconds"
date: 2013-08-31
forum: Hardware
---

### Post by kmYhPsx on 2013-08-31
Hi all,

I need help with my microphone, which is not working. It starts fine when I plug it in but after a few seconds of use (eg. recording or microphone monitoring in Audacity, speaking on Skype, or looking at the input bar bouncing in the Audio controls - before I uninstalled pulseaudio) it stops working. I uninstalled pulseaudio because I had noticed that the mic resumed working after a killall pulseaudio, but it might have been a coincidence, since now I have uninstalled it and the problem remains.

I recently moved to Ubuntu 13.04 with a fresh install. I had had the same problem for a few weeks before (I had the 12 long term release version) but it was stopping to record after minutes, not seconds. The microphone is a Blue Yeti, which seems to work fine on Windows, as it did before in Ubuntu.

As a side note, the internal microphone has a lot of static noise, and gnome-alsamixer doesn't work, so I have to use alsamixer from the terminal.

I tried muting the right channel on the microphone (someone had written to try that in their blog) but didn't change anything. I tried installing qjacktl and ardour to see whether I could use the mic in some other software but I don't really understand how those work (the first somehow installed in German, which I don't speak that well) :-/ 

Here's the alsa-info report. I don't know much about audio drivers, so I don't know how to spot issues from there :(
[http://www.alsa-project.org/db/?f=b7d612ea25a1144b8d9903670623320076b88bf7](http://www.alsa-project.org/db/?f=b7d612ea25a1144b8d9903670623320076b88bf7)

Any help would be greatly appreciated.

Chiara

---

