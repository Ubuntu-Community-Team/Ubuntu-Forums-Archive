---
title: "Creative Zen"
date: 2008-07-14
forum: Hardware
---

### Post by adamant715 on 2008-07-14
Is there any good converter that can convert videos for it?

---

### Post by mcallenSchmee on 2008-07-17
IRiverter works, use the "creative zen vision:m" profile.

---

### Post by ProbablyX on 2008-07-17
```
ffmpeg -i input.file -vcodec rawvideo -pix_fmt rgb24 -r 15 -acodec adpcm_ima_wav -s 128x96 output.avi 
```

I came over that code before, can't guarantee it will work though

---

### Post by adamant715 on 2008-07-18
IReverter worked like a charm. Thanks!

---

