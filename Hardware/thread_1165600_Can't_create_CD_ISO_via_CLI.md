---
title: "Can't create CD ISO via CLI"
date: 2009-05-20
forum: Hardware
---

### Post by Dorzu on 2009-05-20
This is more of a curiosity than anything else. I found a work-around, but I want to understand why my CLI approach doesn't work.

In short, dd/readom/cat don't work for creating a CD ISO on my system. I mounted, unmounted, made sure to mount as ISO9660, did a cdrdao scanbus to check device(there's only one optical drive on my system anyway), ... all of the things that I could evoke from memory. Finally, in a fit of frustration, I used K3b. It worked. I mounted the ISO and it was exactly the disc.

For reference, all three commands had the same behavior. They created a file of ~1.5MB and gave the same error mesage:
cat: /dev/scd0: Input/output error
dd: reading `/dev/scd0': Input/output error
Errno: 5 (Input/output error), read_g1 scsi sendcmd: no error

Any thoughts? I'm not sure if this is symptomatic of a hidden problem.

---

