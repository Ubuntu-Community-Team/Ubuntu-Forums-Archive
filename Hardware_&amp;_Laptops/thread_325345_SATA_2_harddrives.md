---
title: "SATA 2 harddrives"
date: 2006-12-25
forum: Hardware &amp; Laptops
---

### Post by edwells5 on 2006-12-25
sata 2 drives useing edgy 6.10 amd64 

--------------------------------------------------------------------------------
I am A newbie and this is my question i hope i can explain correctly. at 71yrs. it is sometime hard.
is their a problem  in Edgy recogizing and config. Sata 2 drives of the size below and what is the best file format for them. i am having a new computer assembled . mob-Gigabyte K8 Triton AMD64X2 4800+ 4GIG PC3200DDR 400--Geforce 7300 PCIE 256MB DDR2 . I am puting in 3 sata 2 drives . 1 is 160GIG- 2- 300GIG.

---

### Post by futz on 2006-12-25
> **edwells5 said:**
> sata 2 drives useing edgy 6.10 amd64 

--------------------------------------------------------------------------------
I am A newbie and this is my question i hope i can explain correctly. at 71yrs. it is sometime hard.
is their a problem  in Edgy recogizing and config. Sata 2 drives of the size below and what is the best file format for them. i am having a new computer assembled . mob-Gigabyte K8 Triton AMD64X2 4800+ 4GIG PC3200DDR 400--Geforce 7300 PCIE 256MB DDR2 . I am puting in 3 sata 2 drives . 1 is 160GIG- 2- 300GIG.
Should be no problem whatsoever, provided the mainboard has a SATA2 (3.0Gb/s) controller onboard and linux drivers for that controller are there in Edgy. 

From your extremely vague description (K8 Triton) I have no idea which mainboard you have, as Gigabyte lists around 50 different K8 series mainboards. If it only has SATA1 (1.5Gb/s) controller then you'll have to jumper those drives for 1.5Gb/s (SATA1) operation.

The OS doesn't really care what type of drive it is. They all look alike to the OS as long as you have proper drivers for the drive controller that's on the mainboard. The critical thing for drives to be recognized is that proper drivers are in place. 

The new JMicron controller drivers in particular are still pretty flaky, so if that mainboard has a JMicron controller onboard, expect some problems. I've had lots of grief with them.

Best format? Probably ext3. I've used ReiserFS a lot and tho it's fast and good with lots of small files, it's a bit fragile. It can be very very frightening sometimes when it suddenly appears you've lost 320GB of data (acts like complete drive failure) because of Reiser's funny way of doing things. It seems to always fix itself, but needs a complete powerdown and reboot before it happens, so if your reiser drive seems to have died, just power down all the way and reboot. I've switched back to ext3 lately because of this, on the big archive drives especially.

---

### Post by edwells5 on 2006-12-25
> **futz said:**
> Should be no problem whatsoever, provided the mainboard has a SATA2 (3.0Gb/s) controller onboard and linux drivers for that controller are there in Edgy. 

From your extremely vague description (K8 Triton) I have no idea which mainboard you have, as Gigabyte lists around 50 different K8 series mainboards. If it only has SATA1 (1.5Gb/s) controller then you'll have to jumper those drives for 1.5Gb/s (SATA1) operation.

The OS doesn't really care what type of drive it is. They all look alike to the OS as long as there you have proper drivers for the drive controller that's on the mainboard. The critical thing for drives to be recognized is that proper drivers are in place. 

The new JMicron controller drivers in particular are still pretty flaky, so if that mainboard has a JMicron controller onboard, expect some problems. I've had lots of grief with them.

Best format? Probably ext3. I've used ReiserFS a lot and tho it's fast and good with lots of small files, it's a bit fragile. It can be very very frightening sometimes when it suddenly appears you've lost 320GB of data (acts like complete drive failure) because of Reiser's funny way of doing things. It seems to always fix itself, but needs a complete powerdown and reboot before it happens, so if your reiser drive seems to have died, just power down all the way and reboot. I've switched back to ext3 lately because of this, on the big archive drives especially.
REPLY
thank you. The mob is a nForce 4 SLI and the reply was very informitive i hsd on a fourm that ext3 was the most stable.

---

### Post by edwells5 on 2006-12-27
Futz i have computer up and running everything is working perfect. was  able to set up my printer ok stil ned to setup scanner.
Thank you for all you help  Sata 2 drives work  perfect now i have a lot of learning to do. Automatmatix2 installed great and used it to install pkt's for my codecs.
tks a millon. soon to get rid of MS$ on my other computers.
edwells5

---

