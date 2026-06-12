---
title: "Ati Problem!!!!help"
date: 2008-02-20
forum: Hardware &amp; Laptops
---

### Post by devilsrogue on 2008-02-20
I have a ati problem

I have a ati radeon x1600 agp card and if i install the fglrx dirver I get a black screen after reboot! I have tried everything!
I have a 
athlon 64 cpu socket 754
msi k8n-neo platnum
80gb hdd
dvdrw

all else works fine except video and I would love to have 3d acceleration 

I have uninstalled ubuntu and went back to windows until I can find a solution and I want to dump window$ all together

---

### Post by sloggerkhan on 2008-02-20
try getting the latest driver from ati. The packaged driver might not support your card properly.

---

### Post by RavanH on 2008-02-20
Download the latest driver from [http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html) (select your system: Linux x68_64 then you card and click Go)

Then follow instructions on [https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-117effcb5f0fbe8e10f40881bff1dbf7824a77b0](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-117effcb5f0fbe8e10f40881bff1dbf7824a77b0)

Worked for me perfectly :)

---

### Post by RavanH on 2008-02-20
Oh, but you might kill hibernation using the latest driver. At least, i cannot resume from hibernation (and it corrupts the swap partition in the process) so if that is an issue for you, you might want to revert to the open source driver or maybe an older version of the fglrx driver.

Another note: on the instructions page [https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-117effcb5f0fbe8e10f40881bff1dbf7824a77b0](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-117effcb5f0fbe8e10f40881bff1dbf7824a77b0) you will read a lot about disabling composite for the ATI proprietary drivers, but that is no longer needed for the 8.x versions. Also you do not need to get XGL anymore, it works fine with AIGLX now :)

---

