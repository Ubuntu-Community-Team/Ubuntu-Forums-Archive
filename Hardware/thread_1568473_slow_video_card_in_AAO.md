---
title: "slow video card in AAO?"
date: 2010-09-05
forum: Hardware
---

### Post by abelito8 on 2010-09-05
Hi all

I have an Acer Aspire One 160GB, 1RAM and 1.66 Ghz processor and I am running ubuntu 10.4 on it

for some reasons video documents are extremely slow and I cannot watch a video on the full screen at normal speed (if the video takes more than 1/3 of the screen it goes slowly)

is there any way to solve this or it's just my computer that it's not powerful enough....
and in case (for next time I have to buy one) what determines the video speed? I need more RAM or a more powerful processor?

thank you in advance

---

### Post by cascade9 on 2010-09-09
For flash videos, there isnt much on the way opf a cure now (it might help if you run lovinglinuxs 'flash aid', but I dont know). 

As for videos being played of the HDD, CPU matters more than RAM once you've got any decentamount of RAM. EG- I run a  old 'junker' computer as a media player that just doesnt have the CPU power to play 1080p (currently a P4 2.53, 512MB, 6600GT). If I increase the RAM to 1GB or higher, and it still wont play 1080p. 

However, that is just for CPU video decoding. Modern video cards have at least some degree of hardware decoding support (VDPAU for nVidia, XvBA for ATI) and that can drop the CPU requirements a huge amount, as the CPU doesnt need to do the decoding, its shunted of to the video card which has a better capability to decode video. 

People with Intel Atoms (like your acer) and a VDPAU nVidia card can play 1080p videos.

---

