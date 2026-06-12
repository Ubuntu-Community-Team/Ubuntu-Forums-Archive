---
title: "Using one mic into multiple apps at the same time"
date: 2008-10-20
forum: General Help
---

### Post by Manu311 on 2008-10-20
Hi,

I hope this is the correct place for my question:

I used to speak in Ventrilo and Skype at the same time when I had Windows. Both programs are running without problems in my Debian (ventrilo in wine) but not at the same time.
The problem is both of them reserve the output from /dev/dsp (mic) and the other program can not access to this file.
I thought something like linking it to an other file could help.
But I didn't find an answer so far, neither ln nor cat helped me so far. Cat writes something like a record ;) and ln only linked the file, so if the original file is reserved, the link is as well.
I'm searching for this problem for weeks now (google) but it looks like I'm the only one with this problem :(.

Does anyone maybe has an idea?

---

