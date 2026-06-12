---
title: "PCI SATA Controller Sil 3114 max. Harddisk Size"
date: 2009-02-21
forum: Hardware
---

### Post by LippiVan on 2009-02-21
I am using this SATA Controller with 4 500GB Samsung HDs right now, but I need to get more space. 

Is it possible to use the 1,5TB Segate Harddrives (SATA II Seagate Barracuda, 7200.11, 1.5 TB, 32MB Cache)? 
Is there a limited possible HD filesize which the controller can't handle anymore?


I could not find any answers about this in the web, so I'll be very thankfull for any response.

---

### Post by cariboo on 2009-02-21
As far as I know there shouldn't be any limits to the size of drive you can connect to you device. I would stay away from Seagate drives for the time being until they get there firmware problems fixed. Seagate claims they have solved the problem, but I would wait 6 months before purchasing any large drives manufactured by them.

Jim

---

### Post by LippiVan on 2009-02-22
thx a lot for your answer. So you mean I should rather go with another brand, like Samsung oder Hitachi? 

I still have one more question, all these drives are SATAII, my Controller supports only SATAI. Is this going to be a problem, oder does this just mean that the reading/writing speed will be lower? 

thx a lot,

---

### Post by ScaryBob on 2009-07-06
deleted

---

### Post by ScaryBob on 2009-07-06
Some software and hardware has a 2TB limit. I would guess that the Sil 3114 has this limit on individual drives and maybe native arrays. IIRC, I had to fix something in software or on the array (mk2fs maybe???) to get it to work with more than 2TB. That was a while ago so I've lost the details and it may not still apply.

---

