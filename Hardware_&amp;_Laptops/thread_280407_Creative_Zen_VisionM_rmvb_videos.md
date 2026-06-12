---
title: "Creative Zen Vision:M rmvb videos"
date: 2006-10-19
forum: Hardware &amp; Laptops
---

### Post by dyous87 on 2006-10-19
Hello everyone, I recently purchased a Creative Zen Vision:M and it's been working wondefully with Gnomade2.  The only thing I haven't been able to do it yet is transfer videos to it. I converted an rmvb video that I have to avi using mencoder and then transfered it to my Zen using the Gnomade2 data transfer. The video shows up on my Zen under videos but it is unable to play. Does anyone know how to get this working right. Maybe I need to convert it to an mpeg instead, or maybe I'm just not transfering the video correctly. 

Thanks in advance!
--David

---

### Post by ivago on 2006-11-16
Hi,

just try the following options when converting video to your ZVM

```
mencoder file1.avi -o test1.avi -vf scale=320:240 
-oac mp3lame -ovc xvid -xvidencopts bitrate=800
```

it works OK for me

---

