---
title: "no sound"
date: 2009-06-18
forum: Installation &amp; Upgrades
---

### Post by bavman on 2009-06-18
I made a ubuntu cd from the 9.04 iso. And when i run it the sound is messed up....it just sounds funky like during startup. I took the cd to my friends house and had him boot it up and the sound worked perfectly. We were both on hp laptops. Is there something i need to do for the driver or anything?

---

### Post by raymondh on 2009-06-18
> **bavman said:**
> I made a ubuntu cd from the 9.04 iso. And when i run it the sound is messed up....it just sounds funky like during startup. I took the cd to my friends house and had him boot it up and the sound worked perfectly. We were both on hp laptops. Is there something i need to do for the driver or anything?

Same sound cards?  I don't want to sound ***** but my wife and I had his & hers-same-brand/model laptops but each had different components inside.

---

### Post by Mark Phelps on 2009-06-20
> **bavman said:**
> I made a ubuntu cd from the 9.04 iso. And when i run it the sound is messed up....it just sounds funky like during startup. I took the cd to my friends house and had him boot it up and the sound worked perfectly. We were both on hp laptops. Is there something i need to do for the driver or anything?
It's likely the two laptops are using different sound chips, one of which is being detected properly and having the proper drivers loaded, and the other which is not.

The second might require installing OSS (Open Sound System) drivers.  You can find out about OSS stuff by going to the 4front tech site, below:

[http://www.opensound.com/]("http://www.opensound.com/")

---

