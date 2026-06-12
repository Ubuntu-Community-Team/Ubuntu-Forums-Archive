---
title: "Memory Stick Duo Adapter (MSAC-M2) not detected"
date: 2008-05-30
forum: Hardware
---

### Post by vikarama on 2008-05-30
Hi,

I have a Compaq V6211AU laptop and I am running Hardy x86_64. The inbuilt card-reader on my laptop reads all cards but when a Sony's memory stick duo adapter (MSAC-M2...this one [http://www.amazon.com/Sony-MSAC-M2-Replacement-Adaptor-Package/dp/B0000CD7K9](http://www.amazon.com/Sony-MSAC-M2-Replacement-Adaptor-Package/dp/B0000CD7K9)) is inserted nothing happens.

I saw the same issue being reported on System76 laptops, but mine is not a System76 machine.

Could somebody help?

Thanks

Regards,
vikarama

---

### Post by Shpongle on 2009-04-30
im having the same problem, on a toshiba equium a200-1ac, any other card i have tried has worked, it'd be good to have a fix for this

---

### Post by f(x) on 2010-04-19
Same problem here: Toshiba Portege M600. Any updates on this issue?

---

### Post by stefanadelbert on 2010-11-06
I have the same problem. I have an HP Pavilion dv6000 laptop with a built-in reader. The problem is that there is no driver available for the built-in reader that allows Sony Memory Sticks to be mounted. The built-in reader that I have is:

07:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)

You can find out which reader you have by running 'lspci'. You'll find a line similar to the one above.

Until someone reverse engineers the Windows driver or Ricoh provide a Linux driver, you're not going to be able to read Sony Memory Sticks using the Ricoh built-in reader.

Of course, if you have another brand of built-in reader, then there may be some other problem.

---

