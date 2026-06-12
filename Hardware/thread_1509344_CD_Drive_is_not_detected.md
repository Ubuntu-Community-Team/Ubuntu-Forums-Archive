---
title: "CD Drive is not detected"
date: 2010-06-14
forum: Hardware
---

### Post by xeonmax on 2010-06-14
hi all,
I'm using toshiba. i've installed ubuntu 9.10. I've been using my cd drive without any problem till yesterday, but i don't know what happend, my drive is not being detected right now:confused:. It has got no problem with Windows XP. Only ubuntu is not taking CD Drive..
I've a doubt whether I've deleted that drive in disk utility, by mistake...
How can i recover my cd drive....??
Please help me out here....

---

### Post by garvinrick4 on 2010-06-14
> **xeonmax said:**
> hi all,
I'm using toshiba. i've installed ubuntu 9.10. I've been using my cd drive without any problem till yesterday, but i don't know what happend, my drive is not being detected right now:confused:. It has got no problem with Windows XP. Only ubuntu is not taking CD Drive..
I've a doubt whether I've deleted that drive in disk utility, by mistake...
How can i recover my cd drive....??
Please help me out here....

Run this code in your ubuntu, I doubt if you lost it.

```
sudo eject /dev/sdr0
```

 (the number 0 not the letter)

Did it open for you

---

