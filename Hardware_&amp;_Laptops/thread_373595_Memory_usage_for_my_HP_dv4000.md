---
title: "Memory usage for my HP dv4000"
date: 2007-03-01
forum: Hardware &amp; Laptops
---

### Post by neway on 2007-03-01
I am pretty new to linux. Resently I installed edgy on my HP dv4000 laptop. After clean install, the memory usage is about 160 MB. With wireless and samba network, it tooks almost 180MB. Meanwhile it only takes about 80 MB on vmware. 

Is it normal? I heard ubuntu use a lot less memory than XP. However it doesn't seems to be true. Did I miss anything?

---

### Post by lukew on 2007-03-03
> **neway said:**
> I am pretty new to linux. Resently I installed edgy on my HP dv4000 laptop. After clean install, the memory usage is about 160 MB. With wireless and samba network, it tooks almost 180MB. Meanwhile it only takes about 80 MB on vmware. 

Is it normal? I heard ubuntu use a lot less memory than XP. However it doesn't seems to be true. Did I miss anything?

Memory usage is different under Linux; as much memory as possible in order to try and make things as quick a possible. Years ago I used to always 100% memory usage. The swap is different than paging space. Paging space is used as extra memory one the RAM is used up. Linux SWAP is similar but it will actively swap data between swap and RAM if it thinks it is more needed.

Saying all that I run beryl and all the eye candy and never go much above 400MB. My Windows XP laptop at work recently got upgraded from 512MB to 2GB as it was always paging and I have the setting for best performance and no eye candy.

I hope you are enjoying Linux. I hope you have got to the stage when you realise that things are not harder, just different, and different for a good reason.

All the best and don't be scared of asking any more questions; thats the best thing about the ubuntu community; good people looking out for each other.  

Luke

---

### Post by neway on 2007-03-05
Thanks for your reply. Are you saying the Ubuntu will load different module depends on how much physical memory I have?

For example, if I have 512 MB, it might load 150 MB, meanwhile, if I only have 256MB, it will only load 80 MB at start up time?

---

