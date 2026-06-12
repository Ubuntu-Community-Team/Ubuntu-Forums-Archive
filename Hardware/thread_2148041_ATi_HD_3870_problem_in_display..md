---
title: "ATi HD 3870 problem in display."
date: 2013-05-23
forum: Hardware
---

### Post by parantonis on 2013-05-23
Hello everybody I'm new in forum and also in linux,I use linux 12.04 and
my problem is that I have this graphic card
 (PC Partner Limited Sapphire Radeon HD 3870)
 and I cant find a way to install drivers. My computer
 doesnt support high resolution and also
I cant connect a second monitor to my system.
 Please help me if someone have the same problem.

---

### Post by Mark Phelps on 2013-05-24
How recently did you install 12.04? Asking because if it was in the last few months, you are likely to have 12.04.2 -- and that is bad news for you, as it has a newer X-server version that is incompatible with the AMD restricted drivers for the HD 2x/3x/4x series video cards.  In this case, only the default Radeon driver will work -- which you already have installed or you would be seeing a blank black screen after you login.

The LAST Ubuntu version that will work with the AMD restricted drivers and your card was 12.04.1.

---

### Post by parantonis on 2013-05-25
> **Mark Phelps said:**
> How recently did you install 12.04? Asking because if it was in the last few months, you are likely to have 12.04.2 -- and that is bad news for you, as it has a newer X-server version that is incompatible with the AMD restricted drivers for the HD 2x/3x/4x series video cards.  In this case, only the default Radeon driver will work -- which you already have installed or you would be seeing a blank black screen after you login.

The LAST Ubuntu version that will work with the AMD restricted drivers and your card was 12.04.1.

Yes I have 12.04.02 do you think that if I install 12.04.01 it will be ok ?

---

### Post by Mark Phelps on 2013-05-25
[LIST=1]
[/LIST]
> **parantonis said:**
> Yes I have 12.04.02 do you think that if I install 12.04.01 it will be ok ?

Yes, that original 12.04 has the older X-server version which still works with the AMD legacy restricted drivers.

---

### Post by parantonis on 2013-05-25
> **Mark Phelps said:**
> 

Yes, that original 12.04 has the older X-server version which still works with the AMD legacy restricted drivers.

And I have to find the Drivers for my card or its pre-installed ? And do you also know if my card works fine in ubuntu 13.04?

Thanks in advance and sorry for all these questions!

---

