---
title: "HD spindown/hdparm"
date: 2007-10-18
forum: Hardware &amp; Laptops
---

### Post by jnusa on 2007-10-18
In my quest to spin down my raid, and no apparent methods work while the raid is created (meaning that my Adaptec 2610sa doesn't support too many hdparm/sdparm commands), I'm thinking about disecting my raid and try to set standby mode manually on each harddrive with hdparm and create the raid again. My question whether or not this will work? It seems like that the settings that hdparm set, is solely in the harddrive and it is 100% responsible for controlling the spindowns/spinups based on activity. Is this assumption correct? Or will this simple not work, unless I get a controller which supports spindowns. 
Just for the record - the raid is only for storage and the OS is stored on a seperate disk. So no logs or similar is written to the raid on a regular basis. Also the raid is only accessed a couple of times a day - So lifetime issues are not a problem. 

My hardware is an Adaptec 2610sa (Dell OEM rebrand) and 6xSamsung T166, RAID5

Any information is greatly appresiated!

/jnusa

---

