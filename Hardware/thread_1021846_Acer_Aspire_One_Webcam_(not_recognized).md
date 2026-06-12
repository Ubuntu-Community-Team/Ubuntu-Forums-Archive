---
title: "Acer Aspire One Webcam (not recognized?)"
date: 2008-12-26
forum: Hardware
---

### Post by stargirl51 on 2008-12-26
Hi,

I just bought a new Acer Aspire One with the following specs:

Acer Aspire One ZG5
Intel Atom CPU 1.6 GHz
160 GB HDD
1 GB RAM
6-Cell Battery
0.3 MP Webcam

Out of the box, I reformatted the laptop with Ubuntu 8.10 (Originally Windows XP). The install was perfect, but the webcam will not work on web-based messenger services, such as Meebo. I ran the following codes in terminal:

sudo apt-get install luvcview
dmesg |grep -i "uvc"
luvcview -f yuv

And I was able to see myself on the webcam. However, no matter what I try, I still can't get it working on Meebo.

Any and all suggestions on what to do are greatly appreciated. Thanks in advance!

Cheers,
stargirl

---

### Post by teaker1s on 2008-12-30
[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

be sure to check out hard drive load cycle-or you will kill your drive

---

