---
title: "Two NVIDIA cards -&gt; second one often not detected"
date: 2010-09-26
forum: Hardware
---

### Post by JohannesD on 2010-09-26
Hi!
I have a strange problem and no clue how to solve it. I have two PCIe cards by Club 3D, both with the 9500GT chip. To the first card, my two screens are attached showing the desktop. To the second card, my TV is connected. To watch something, I usually start a second X-Server using the console. I had a similar setup some years ago with an old ubuntu version. It worked perfectly.

Some month ago, I installed Lucid Lynx. The strange thing is, that the second card is very often (but not always) not detected. Although it is listed by lspci, it does not appear in the nvidia-settings program, and starting of the second x server fails (output attached to this post). I also attached the output of dmesg for both cases (card was detected/not detected). 

I have a 32bit processor, 4GB RAM, each card has 512MB memory. This works fine due to PAE. However, I removed 2GM RAM in order to test, if something would change, but no... I also swapped the slots of both cards on the mainboard, (re)installed the recent nvidia driver (vers. 260) and changed some settings in the BIOS... without any success.

Are there any other log-files that could help? Does anyone have an idea, what could cause this problem? I don't understand, what the successful detection of the card is depending on (it seems to be luck).

Thank in advance for any hints.
Johannes

---

