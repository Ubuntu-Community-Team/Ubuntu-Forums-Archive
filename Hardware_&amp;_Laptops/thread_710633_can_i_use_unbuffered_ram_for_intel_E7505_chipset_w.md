---
title: "can i use unbuffered ram for intel E7505 chipset with dual Xeon 2.8Hz"
date: 2008-02-28
forum: Hardware &amp; Laptops
---

### Post by pliu18 on 2008-02-28
i have just purchased a second hand HP Workstation xw6000 running dual xeon 2.8hz [http://h18000.www1.hp.com/products/..._na.HTML#Memory](http://h18000.www1.hp.com/products/..._na.HTML#Memory). i am planning to setup the system to run ubuntu to do some computation work using matlab. i will need to add some more memory to the system. my question is can i use standard unbuffered ram (assuming i don't care too much about reliability)? or do i need to use registered and ECC ram only. i know a lot of the server guys use registered and ECC for reliability but that's not a big concern for me.

the xw6000 uses the intel E7505 chipset and according to the intel webpage i can use "Unbuffered or registered DDR memory".

any help or hints would be greatly appreciated.

---

### Post by Yellow Pasque on 2008-02-28
Hi Philip. You shouldn't mix ECC and non-ECC RAM. You must use all ECC or all non-ECC.  Mixing might work, but it is not recommended or supported by HP.
> Some models support ECC memory and non-ECC memory. Other models support only non-ECC memory. For those systems that do support ECC memory, HP does not support mixing ECC and non-ECC memory. Doing so will cause the system to blink the Num Lock LED on non-USB keyboards continuously and, if a speaker is installed in the system, there will be a short beep followed by two long beeps. In addition, the system will not boot the operating system.
[http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?lang=en&cc=us&taskId=130&prodSeriesId=295779&prodTypeId=12454&prodSeriesId=295779&objectID=lpv38838](http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?lang=en&cc=us&taskId=130&prodSeriesId=295779&prodTypeId=12454&prodSeriesId=295779&objectID=lpv38838)

---

