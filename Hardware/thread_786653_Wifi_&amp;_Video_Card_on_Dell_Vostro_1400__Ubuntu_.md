---
title: "Wifi &amp; Video Card on Dell Vostro 1400 / Ubuntu Hardy 64 bits"
date: 2008-05-08
forum: Hardware
---

### Post by Malawi on 2008-05-08
Hello,

I have a problem with my very new computer, I do not have the wifi (card not detedted, a Broadcom Bcm43xx, 4310 I think). I have install fwcutter and b43-fwcutter by hand, but it does not change anything. I also have test under Backtrack (2 and 3 Beta). It is not detedted neither.

Moreover, my video chart (Intel® Graphics Media Accelerator X3100) does not seem to be detedted neither (with Hardware Drivers/Properties). The screen works well, but when I connect the PC on a TV, there is nothing on the TV screen (even with Fn+F4).

Where do these problems come from? I do not find the solution. If somebody met this problem, thank you to answer me...

---

### Post by omegamike3 on 2008-05-19
I suppose there could be issues with 64bit and the Intel drivers. I'm only running 32bit on my 1400, so I couldn't really tell you more than in 32bit things, video-wise, are working beautifully. You can even now have video playing with Compiz enabled without any hacks or being limited to certain codecs. As far as wireless in 32bit, ndiswrapper is still the way to go. The drivers that are installed by default are by far the best to be made available yet, but there have still been some connectivity and speed issues, in my experience.

---

