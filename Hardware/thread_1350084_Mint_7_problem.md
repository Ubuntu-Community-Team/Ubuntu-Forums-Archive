---
title: "Mint 7 problem"
date: 2009-12-08
forum: Hardware
---

### Post by hoosemon61 on 2009-12-08
Got no response to the following post on the Mint forum, so I thought I'd try here.

Only additional info since I wrote the post below is that I ran Memtest and it passed.

=========================================


I bought a used P4 2.6Ghz computer with an ABit MOBO.

It has 1.2GB Ram installed and a graphics card (NVidia) that has, I believe 512MB of onboard RAM (not sure without opening it).

I was using the on-board sound, but installed a Creative 7.1 card I had on hand in the course of chasing this problem.

I installed Mint 7, and have been using it very successfully to surf, move files to and from MP3 players and even access shared files on my Windoze machines through my home network.

I found a problem when I started watching streaming shows on HULU.

The sound and picture are fine. No sign of lag, jumping or poor quality, even on full screen mode.

After several minutes of play, however, the sound started oscillating like a machine gun sound, and eventually (1-2 minutes more) the picture will freeze, then even the mouse freezes after another 5-10 minutes.

Reboot will allow me to start over, but it all happens again in about the same amount of time.

I figured I had a bad chip in the on-board sound or something, so I tried a Creative 7.1 board I had laying around. I disabled the on-board sound, and Mint recognized the new card right away.

It sounded great and seemed to work fine, but streaming video did exactly the same thing.

I can play an audio file for 2 hours straight without a hitch, so I'm doubting the sound card.

At this point I'm thinking possibly video card, until I get it to freeze by downloading 22 podcast files simultaneously (forgot to set the limit on GPodder).

So, I try both of these activities again, this time watching the system monitor. In both cases, the CPU usage is between 85% and 100% steadily for 5-6 minutes before lock up. Memory usage never even spikes above 25% during this time.

So...I'm thinking temperature.

I can check the CPU temp if I enter the BIOS on reboot, so I check right after a freeze and it's within a couple degrees of the max listed in the BIOS.

I add a rear case fan and make sure that one and the front fan are both blowing out. I have the CPU fan pulling air in and blowing it onto the heat sink (a big copper unit). It has a hood/tube that's attached to the side cover, so it pulls outside air, not from inside the case. I also removed the sink and scraped off most of the glopped on paste, leaving just a very thin layer as recommended.

This seems to make the unit run cooler (when I check the BIOS), but I'm able to crash the system again with a big download. Even though the streaming video lasts longer, it too crashes eventually.

Anyone have any bright ideas where to look next?

As I said, low bandwidth usage seems to be no problem.

Thanks,

Hoosemon

---

### Post by drifter2502 on 2009-12-09
I am not very tech minded but I had a similar problem in 9.04 and found it to be a codex problem and nothing to do with hardware.

---

### Post by hoosemon61 on 2009-12-10
Thanks Drifter, I'll look into that.

Hoosemon

---

