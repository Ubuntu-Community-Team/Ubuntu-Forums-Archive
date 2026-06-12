---
title: "AMD core CPUs question"
date: 2018-05-07
forum: Hardware
---

### Post by ra7411 on 2018-05-07
AMD makes  CPUs with various numbers of cores:  4, 6, 8 that I've seen for sale.

I came across an article somewhere saying Windows isn't set up to use more than 4 optimally.

Does anybody have info or a guess, as to what number of cores Ub 16.04, Ub 18.04  can use optimally?

Thanks

---

### Post by QIII on 2018-05-07
I'm not sure where you might have read that.

Out of the box,  64 bit Windows 10 supports 256 cores, Ubuntu supports 512.  Both support kernel flags to support many more.

My daily driver sports 16 cores/32 threads.  I run a lot of Virtual Machines that take up a lot of that.

Whether or not anything more than 4 cores is of value to a casual user is debatable.  I don't think it's worth it if what a user is doing consists of much more than browsing and productivity apps.  Neither of those benefits from a surfeit of threads.

---

### Post by Yellow Pasque on 2018-05-09
It depends on the workload too: [https://www.phoronix.com/scan.php?page=article&item=amd-ryzen-cores&num=1](https://www.phoronix.com/scan.php?page=article&item=amd-ryzen-cores&num=1)

---

### Post by Autodave on 2018-05-09
I have an 8 core AMD. When doing simple things (and logging core usage) I might see one or two cores running at 15-20% while the other ones pretty much stay around zero. But once a core reaches about about 20% or higher, other cores start doing more. I have seen all 8 running near 100% while gaming (with corresponding roar from cooling fans).

---

