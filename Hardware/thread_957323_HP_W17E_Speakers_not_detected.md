---
title: "HP W17E Speakers not detected"
date: 2008-10-24
forum: Hardware
---

### Post by RES123 on 2008-10-24
Hi All,

I have an Acer Aspire with an HP w17e monitor lashed to it.

The W17E has it's own speakers and are recognized by Knoppix but not by Ubuntu.  Is there any way to get support for these into Ubuntu.

Thanks In Advance, 
Bob S.

---

### Post by kpkeerthi on 2008-10-24
Make sure your audio hardware is listed in the output of below command:
```
lspci
```

If it is listed, it could be that it is muted. Open [alsamixer]("http://en.wikipedia.org/wiki/Alsamixer#General_Controls") from a terminal and check the channel volumes and make sure master and pcm are not muted.
```
alsamixer
```

---

