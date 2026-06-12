---
title: "linux or xp?"
date: 2008-12-04
forum: Hardware
---

### Post by curiouscustomer on 2008-12-04
i was trying ubuntu 8.10 but i was having trouble installing my network card. so i installed XP at least temporarily. will ubuntu be better faster and stronger or should i stick with xp?

i guess i will have to reinstall ubuntu to see for myself and i can probably finally get an internet connection if i try again. 

does anyone have an opinion?

i mean i have only an 8 gig hard drive 320 ram and a slow slow pentium II processor so i guess i can't expect much from any OS. or can I?

---

### Post by stefangr1 on 2008-12-04
> **curiouscustomer said:**
> i was trying ubuntu 8.10 but i was having trouble installing my network card. so i installed XP at least temporarily. will ubuntu be better faster and stronger or should i stick with xp?

i guess i will have to reinstall ubuntu to see for myself and i can probably finally get an internet connection if i try again. 

does anyone have an opinion?

i mean i have only an 8 gig hard drive 320 ram and a slow slow pentium II processor so i guess i can't expect much from any OS. or can I?


You can't expect "much". However, I think with your specific configuration Ubuntu (or for slightly better performance, try Xubuntu!) is just proportionally slower then faster systems, whereas windows-xp with all the virus-scanners and service packs will be completely unworkable. Be sure to configure enough swapspace, a few times your RAM in your case. In that case, you will have about 4-5 gig left after a complete install.

---

### Post by TyTiger on 2008-12-04
Linux. :P

Performance differs between Linux and Windoez because Windoez Pre-loads common applications in to RAM, however the drawback for this is you have less ram to do other things so although it appears faster, your really just running loaded applications out of the RAM which in most cases does have a faster transfer speed than your Hard Drive.

Linux does not pre load apps in to Ram, but this has an advantage. 
You may have to wait a few more seconds for your application to load, but compared to windoez your application will run allot smoother. This i have seen by running the labour-intensive 3D application Second Life. On windows it typically runs more choppy and 'Lags out'

Running this application on the same PC using ubuntu ~(With nVidia Restricted drivers) the application runs far smoother and frame rate is allot higher even in situations where it would suffer lag running under Windoez. 

PS. What is yoru network card? Chipset and all. You can find this out by typing
```
lspci
```

in your terminal and searching the list for any key words relating to Network

---

### Post by stefangr1 on 2008-12-04
Linux also preloads in the RAM. My experience on a p-III 1000Mhz system with 256mb ram and windows xp is that is works fine without service packs and a virusscanner, but when you fully configure it, you have to turn the computer on before taking a shower and breakfast if you wan't to start working afterwards. So on a P-II system that will be even worse. A friend of mine has a P-II 233Mhz system with 192mb RAM, that runs Xubuntu, and that is very workable. Even though it is off cause much slower than a modern system.

---

### Post by TyTiger on 2008-12-04
> **stefangr1 said:**
> Linux also preloads in the RAM. My experience on a p-III 1000Mhz system with 256mb ram and windows xp is that is works fine without service packs and a virusscanner, but when you fully configure it, you have to turn the computer on before taking a shower and breakfast if you wan't to start working afterwards. So on a P-II system that will be even worse. A friend of mine has a P-II 233Mhz system with 192mb RAM, that runs Xubuntu, and that is very workable. Even though it is off cause much slower than a modern system.

there is an application for linux that can pre load common applications in to Ram the same way windows does, but its not installed by default to my knowlege

( preloader )

---

### Post by stefangr1 on 2008-12-04
> **TyTiger said:**
> there is an application for linux that can pre load common applications in to Ram the same way windows does, but its not installed by default to my knowlege

( preloader )

Well, it is a little off topic, but if I look at my memory usage by typing either "free" or "top" I see that almost my entire memory is used for caching, and I didn't install anything for that. That's why more RAM is always better.

---

