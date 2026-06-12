---
title: "linux on an mp3 player..."
date: 2005-12-06
forum: Hardware &amp; Laptops
---

### Post by Haegin on 2005-12-06
I'm saving up for a 30GB philips hdd mp3 player which I hope to get with xmas money and as I can't forsee myself needing 30gb (but as prices don't vary too much at the lower price ranges I am getting it anyway) I am wondering how possible it would be to use 10 gb as a linux partition (with it mounting the 20 gigs on my home folder so i can get my music and so i can store docs there (so that they r accessible on windows))

Any ideas how?

---

### Post by moberry on 2005-12-06
If it mounts as a mass storage device you are golden. Format it in FAT32 (vfat under linux) These partitions cannot exceed 32gb but that does not apply to you. I would not try partitioning into two partitions the firmware of the player might not be able to figure that out.

---

### Post by Haegin on 2005-12-06
Thanks, but im still confused as to how I install linux on it but still have windows pick it up without throwing a fit and without it trying to play the contents of /usr/bin or something equally stupid?

Thanks for the prompt reply

---

### Post by aysiu on 2005-12-06
You want to install Linux (the entire operating system) on the MP3 player, **or** you want to install something so both Linux and Windows can use files on the MP3 player?

If it's the former, I'd highly advise against it.
As moberry mentioned, even with a clean repartitioning, the very fact that the device is partitioned might screw up the way it's read or the way it operates. Also, you'd have to find a way to boot from the device and the particular partition you want it to boot from.

If it's the latter, do nothing. As long as it's formatted as FAT32 or FAT16, both Linux and Windows should be able to read from and write to it.

---

### Post by Haegin on 2005-12-06
I was planning to install the os on it (as its something with a large enough hard drive that I will carry with me almost everywhere there is a pc). I was wondering if there was a way to ensure it remains working as an mp3 player (with an apparently smaller hard drive) but with the ability to use it as a removable hdd with linux installed.

Oh well - hope doesnt make all things possible

---

### Post by aysiu on 2005-12-06
Well, you're certainly welcome to try it, as long as you have your songs all backed up.

I will say that it can be done. However, the only time I've seen it done is the director of our IT department trying to partition his iPod Shuffle to be half iPod and half Damn Small Linux. It took quite a bit of tinkering for him to get it to work exactly the way he wanted it, and he's no slouch when it comes to technology.

---

### Post by Ufo on 2005-12-07
I am writing this post from Damn Small Linux embedded running from iRiver MP3 player inside Windows (because I am at work). Installing DSL embedded in MP3 player was very easy. I just copied DSL embedded files into MP3 player. There was still room for music files too and it works as MP3 player, or ogg player to be precise, just like before. Only thing is that running DSL embedded is lot slower than liveCD and of course installation to hard dirve. But anyhow it works :p

---

### Post by aysiu on 2005-12-07
[QUOTE=Ufo]I am writing this post from Damn Small Linux embedded running from iRiver MP3 player inside Windows (because I am at work). Installing DSL embedded in MP3 player was very easy. I just copied DSL embedded files into MP3 player. There was still room for music files too and it works as MP3 player, or ogg player to be precise, just like before. Only thing is that running DSL embedded is lot slower than liveCD and of course installation to hard dirve. But anyhow it works :p[/QUOTE] Embedded is a totally different story. I was talking about repartitioning your MP3 player so that half is the actual player and half is Linux and then being able to boot from the Linux partition of that USB drive.

---

