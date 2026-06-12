---
title: "HP Pavillion 6040 AMD Turion X2 Tl-52 Processor Ubuntu Feist Fawn Does Not Start"
date: 2007-04-23
forum: Hardware &amp; Laptops
---

### Post by thinkjones on 2007-04-23
Hi, 

I have a HP Pavillion 6040 Laptop with AMD Turion X2 Tl-52 Processor, I have downloaded and burned the AMD 64 ISO (ubuntu-7.04-desktop-amd64.iso) installation.  I have run and checked the disk for errors and t is error free.  

The Ubuntu Feist Fawn just does not start.  I get to the main menu, select "Start or Install" first option, it goes through a few checks then stalls on "Checking Hardware Somtheing or Other".

Does anyone else have problems with Pavillion laptops and or AMD X2 64bit processors?

Thanks
Gene

---

### Post by dizzyreed on 2007-05-03
> **thinkjones said:**
> Hi, 

I have a HP Pavillion 6040 Laptop with AMD Turion X2 Tl-52 Processor, I have downloaded and burned the AMD 64 ISO (ubuntu-7.04-desktop-amd64.iso) installation.  I have run and checked the disk for errors and t is error free.  

The Ubuntu Feist Fawn just does not start.  I get to the main menu, select "Start or Install" first option, it goes through a few checks then stalls on "Checking Hardware Somtheing or Other".

Does anyone else have problems with Pavillion laptops and or AMD X2 64bit processors?

Thanks
Gene

On boot press "e" and add in final line "noapic" and "nolapic"

---

### Post by WolfHeart on 2007-07-05
I have a dv9000series laptop and have been browsing this forum looking for an answer to the exact same problem, why it doesnt boot. So i see everyone recommending those parameters, so i just wonder, what is the noapic and nolapic? what do they do?

---

