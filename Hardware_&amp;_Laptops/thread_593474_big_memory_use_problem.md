---
title: "big memory use problem"
date: 2007-10-27
forum: Hardware &amp; Laptops
---

### Post by adem666 on 2007-10-27
i installed kubuntu-7.10. and I just realized, O.S. allocates big memory. I have 1GB ram. kubuntu always allocates nearly all of them. 

```

# free

output:
             total       used       free     shared    buffers     cached
Mem:       1034176     998544      35632          0      73600     627776
-/+ buffers/cache:     297168     737008
Swap:      1204864      34796    1170068

```

so that, when i run new program, it s start using swap memory. and, it takes time to opening. is it normal ? in windows, maximum using memory is 500 mb - 700 mb. but, in kubuntu, even in stand mode, 950mb ram is using. and, also i think this makes low batery time.

---

### Post by kerry_s on 2007-10-27
yes, it's normal. linux makes use of ram, unused ram is wasted ram. kde is a heavy desktop that loads alot of stuff. you can fine tune swappiness so it uses ram more, google is your friend.

---

