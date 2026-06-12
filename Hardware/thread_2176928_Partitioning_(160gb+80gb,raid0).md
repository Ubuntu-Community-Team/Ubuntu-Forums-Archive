---
title: "Partitioning (160gb+80gb,raid0)"
date: 2013-09-26
forum: Hardware
---

### Post by georges-langlois on 2013-09-26
Hi,

I've used Ubuntu 12.04 Alternative install in order to set raid drives as I've seen in some tutorials. So, I didn't know very well what to do because they've always used identical HDs so I've set like this:
Samsung (80gb) - I've reserved 79gb for raid0 and 1gb for swap
Maxtor (160gb) - I've reserved 79gb for raid0 and 1gb for swap and formated as ext4 the rest of it.

It's a mess, I know.. But i've done just for a test since I've read raid need identical sizes and I didnt want to loose the rest of 80gb in Maxtor. 
In a first moment, when I was reading about raid0 , I couldn't make it work by hardware with my Asus p4s8x-x, but both HDs are connected in a dedicated IDE plug yet (not sure if it helps). I've done ubuntu benchmark tests in each of the drivers:
Maxtor - Average Read: 61,4Mb/s ; Average Access Time: 15,4m/s
Samsung - Average Read: 49,8Mb/s ; Average Access Time: 13,2m/s
RAID - Average Read: 92,4Mb/s ; Average Access Time: 12,5m/s

So, I'd like to ask what would be the best partitioning config for this scenario? I don't care about redundancy. I'd like to have all merged (as one HD but one partition for SO and another for files) and with maximum perfomance.

Thanks in advance for any reply

---

