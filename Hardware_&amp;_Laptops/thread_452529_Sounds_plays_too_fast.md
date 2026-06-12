---
title: "Sounds plays too fast"
date: 2007-05-23
forum: Hardware &amp; Laptops
---

### Post by j00z76 on 2007-05-23
Hi,
I have installed Kubuntu Feisty on a Compaq Evo machine. The kernel I'm using is 2.6.17-11-generic #2 SMP Tue Mar 13 23:32:38 UTC 2007 (from uname). Everything works as expected, but not sound. When I play an MP3 file, the sound is noticeably faster, as if the sampling rate was wrong (hoarse voices sound quite high-pitched, drum beats are faster than they should etc). If you're into Tom Waits, it is a bit of a nuisance :p Normal voices sound like the chipmunks or something like that.

I have tried using amarok with the Xine plugin and  ALSA and OSS outputs, but to no avail. I have also tested mpg321, and the problem is still there. 

 I use the following card (from lspci):
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAMAC'97 Audio (rev 12)
and the snd_intel8x0  driver is loaded into the kernel.

There are comments on  [t_his lkml message_]("http://lkml.org/lkml/2004/2/7/68"), which however refers to an early 2.6 release candidate kernel from some 3 years ago.

Any ideas?
Cheers,
Jose

---

