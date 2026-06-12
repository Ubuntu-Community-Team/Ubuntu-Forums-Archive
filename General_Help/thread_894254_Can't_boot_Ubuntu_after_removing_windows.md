---
title: "Can't boot Ubuntu after removing windows"
date: 2008-08-19
forum: General Help
---

### Post by subehsharma on 2008-08-19
Hi..I've installed Ubuntu(Hardy Heron) from wubi. Although installation was smooth and much easier than Windows but the issue i'm facing is that now if i remove windows and run Ubuntu it won't boot and give some fill missing error. 

I installed windows again and copy two wubi files i.e wubildr.mbr and wubildr and now ubuntu works. 

I know its a bootloader issue but as i'm new to Linux world. Can somebody explain step-by-step solution to resolve this problem.

Thanks..

---

### Post by Orlsend on 2008-08-19
How did you remove windows exactly? Have you read the Wubi Fag about complete full Install?

---

### Post by subehsharma on 2008-08-19
I simply erased the windows partition from Ubuntu.

---

### Post by minhmeoke on 2008-08-19
Wubi lives on the windows partition and requires the windows bootloader to run, so erasing the windows partition will also wipe out ubuntu. Instead, you should try the lvpm utility ([http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)), or do a standard installation to a dedicated partition then copy over your data.

[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?)

---

