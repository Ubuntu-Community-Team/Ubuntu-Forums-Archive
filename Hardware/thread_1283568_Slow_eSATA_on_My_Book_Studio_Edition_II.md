---
title: "Slow eSATA on My Book Studio Edition II"
date: 2009-10-05
forum: Hardware
---

### Post by JurijTurnsek on 2009-10-05
Hi.

I just bought My Book Studio Edition II 2tb with eSATA being one of the decisive features, only to find it being even slower than USB 2.0.

I use the external disc in a RAID 1 configuration (done via supplied software on a windows machine, the partition is therefore ntfs).

I am very disappointed because of this, because if I can't get it to work properly, I just wasted somewhere around 50€, which is a substantial amount in this purchase. On top of that, I'd really need the added performance for video editing.

I use Kubuntu and am backing up my files with Grsync. My laptop is HP dv5t series. Can anyone suggest what to do?

---

### Post by kavon89 on 2009-10-05
Your problem is that you've got it set up for RAID 1 and expect high speeds. The external drives will be much quicker and make more use of eSATA's speedy connection if it's set up as RAID 0.

---

### Post by JurijTurnsek on 2009-10-05
I find that a good enough explanation, except for one thing: why is USB 2.0 faster on the same configuration?

---

### Post by kavon89 on 2009-10-06
> **JurijTurnsek said:**
> Why is USB 2.0 faster on the same configuration?

How much faster?

---

### Post by JurijTurnsek on 2009-10-07
> **kavon89 said:**
> How much faster?

not much, they both reach a top speed of around 25mbs, but usb seem to get there faster, while esata can get to around 27mbs... kinda pathetic

---

### Post by kavon89 on 2009-10-07
Hrm... often the transfer speed gauges are inaccurate. I've seen some crazy speeds like 90MB/s reported on some flash drives, which is impossible.

---

