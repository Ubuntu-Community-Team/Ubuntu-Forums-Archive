---
title: "Volume Control not working in Kubuntu"
date: 2007-07-22
forum: Hardware &amp; Laptops
---

### Post by tafkamk on 2007-07-22
I rencently installed Kubuntu and am loving it, however one things been driving me nuts

I'm using a DFI Nvidia Nforce 4 motherboard which has digital output(realtek ALC850), I managed to get digital output working, but changing master or PCM volume in kmix or even amixer has no effect on volume at all.I have gone through and tried changing volume level on each individual channel listed but not one seems to effect volume, The odd part is volume in Amarok or VLC works great. I've stumbled across varying posts in regards to this issue but nothing seems to help.

Any ideas?

---

### Post by cyb3rj on 2007-07-22
I had a similar problem a while ago.  My solution was to edit the alsa.conf so that it would know about the digital sound.  I could then get my volume controls to work.  Sorry for the lack of specificity; but I hope that gives you some leads to search for a solution.

---

### Post by tafkamk on 2007-07-22
Thanks for your reply

I was reading something about changing the device # in alsa.conf from 0 to 2 however upon doing so I get no sound at all.

---

