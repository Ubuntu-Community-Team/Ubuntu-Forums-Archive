---
title: "known issues with new (11.6) ATI proprietary driver?"
date: 2011-06-26
forum: Hardware
---

### Post by cannonballsimp on 2011-06-26
Hello

I am having minor graphical glitches (similar to the symptoms described in [COLOR=Blue]_[this]("http://ubuntuforums.org/showthread.php?t=1750702&highlight=natty+alt+tab")_[/COLOR] thread) and I am considering getting the new (release date 15 June) ATI driver, in the hope of driving them out. I wondered if there were any known issues with this driver. My graphics card is a Radeon HD4850.


many thanks
Simon

---

### Post by jerrrys on 2011-06-26
some info here

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Radeon+HD+4850&sa=Search&cof=FORID:9#926](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Radeon+HD+4850&sa=Search&cof=FORID:9#926)

---

### Post by silex89 on 2011-06-26
I installed Catalyst and the .mp4 files I had in HD (720p and 1080p) didn't run smooth. The quality is great but the videos play like a 10 fps webcam....

I think I'm having some sort of "extra" issue or bug, but I won't complain because the xf86-video-ati driver is OK for now :)


Regards :D

---

### Post by Yellow Pasque on 2011-06-26
To get video acceleration, you need the xvba-video package from SDS, libva from SDS, and a player built against that libva. See: [https://launchpad.net/~dtl131/+archive/catalysthacks](https://launchpad.net/~dtl131/+archive/catalysthacks)
Note that the packaging isn't perfect, but I'm holding off on fixing it until I see if the libva changes from SDS get merged upstream.

---

