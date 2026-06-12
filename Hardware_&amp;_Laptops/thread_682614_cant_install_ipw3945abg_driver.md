---
title: "cant install ipw3945abg driver"
date: 2008-01-30
forum: Hardware &amp; Laptops
---

### Post by gkjau on 2008-01-30
my ipw3945 is runnig with vista driver(as ubuntu said me)...ubuntu 7.10
i want to install a linux driver for it but i looked in some foruns but couldnt find one that solved my problem....
thankss

---

### Post by jeffus_il on 2008-01-30
Here it is:
[http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2259&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21](http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2259&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21)

---

### Post by patrickfromspain on 2008-01-30
I think you are wrong, ubuntu gutsy already has a linux native driver for that card.

lsmod | grep 3945 should return iwl3945 or ipw3945, since those are the native drivers.

---

### Post by gkjau on 2008-01-30
you are rigth patrick.....sorry
i downloaded the driver but what i have to do now?
im learning how to use linux...
i downloaded it and typed 
# tar -xvzf iwlwifi-1.0.0-1.tgz
files were unpacked
what should i do now?

---

