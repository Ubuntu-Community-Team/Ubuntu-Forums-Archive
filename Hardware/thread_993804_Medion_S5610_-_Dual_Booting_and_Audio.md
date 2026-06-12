---
title: "Medion S5610 - Dual Booting and Audio"
date: 2008-11-26
forum: Hardware
---

### Post by Stephen_at on 2008-11-26
I recently got a Medion S5610 which I'm very pleased with. However I wanted to be able to dual boot it with Vista for various reasons.

Once I'd got it dual booting I had a couple of issues with the sound but I've fixed those so I thought I'd document the process here.

**Dual Booting**
I'd noticed on a previous laptop that the Ubutnu disk partitioner would think it could shrink the Vista partition and then it would stop half way through saying it had failed and by that time it was too late and Vista was lost. So I've found this way works.

The Medion has a primary partition of approx 290GB (The rest being a FAT32 Rescue partition)

1) Get Vista up and running and then defrag the drive using the Vista Defrag.
2) Once the Defrag has completed go into Vistas Disk Management and right click on the Primary Partition and select Shrink Volume. Do NOT shrink the volume, simply make a note of how how small it thinks you can make the Vista Primary Partition.
3) Boot off the Ubuntu CDROM and do the install
4) When it gets to the partitioner It will suggest taking huge amounts of space for Ubuntu but from experience that can mess things up.
5) Slide the bar so that the Vista Partition is as big (or bigger) than the minimum size Vista suggested.
6) Let the installer complete

**Audio**
The S5610 has the ALC888 chipset in it and it supports HDMI audio out as well as the usual jack sockets. By default (or it was in my case) the audio doesn't work too well under Ubuntu (very quiet) and the headphones do not work. But with a little bit of tweaking you can get a good volume and the headphones work and mute the internal speakers.

1) Start a terminal
2) Sudu vi /usr/share/alsa-base/alsa.default
3) Add the following at the end of the file: **options snd-hda-intel model=3stack-dig**
4) sudo /etc/init.d/alsa-utils restart
5) Right click on the volume control and select preferences
6) Select the Device and Track to Control as : HDA Intel (Alsa Mixer) and **Front **
7) Close the preferences

You should now find that the volume control works properly and that plugging phones in mutes the internal speakers.

You should also find that Fn F10 toggles MUTE on and off.

I have found though that sometimes when I've rebooted I need to basically take the volume control up to max and then reduce it to get any audio out.


But I hope this helps

---

