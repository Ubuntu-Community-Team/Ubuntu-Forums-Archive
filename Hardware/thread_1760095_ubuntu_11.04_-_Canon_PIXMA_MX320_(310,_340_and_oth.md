---
title: "ubuntu 11.04 - Canon PIXMA MX320 (310, 340 and others)"
date: 2011-05-16
forum: Hardware
---

### Post by _-LC-_ on 2011-05-16
Hi,

I'm running Ubuntu 11.04 64bit. I would love to be able to print&scan with my Canon PIXMA MX320. Unfortunately Ubuntu doesn't find drivers. The ones from Canon (deb-packages cannot be installed - 32bit + failing dependencies on many core-libs) and the sources don't compile. On older Ubuntu versions (or 32 bit) this doesn't seem to be an issue.
Is there any chance the Canon PIXMA MX3?? series will be usable again?

Thank you for taking some time!

---

### Post by K-Jtan on 2011-06-15
Hi,

I'm having the same problem, but on a 32 bit version. I still have my Ubuntu 10.10 partition where I can use my printer. Is there a way that I could take the driver files and copy it on my new partition? I might be able to help L-C with this after.

Thanks you guys

---

### Post by _-LC-_ on 2011-06-16
> **K-Jtan said:**
> Hi,

I'm having the same problem, but on a 32 bit version. I still have my Ubuntu 10.10 partition where I can use my printer. Is there a way that I could take the driver files and copy it on my new partition? I might be able to help L-C with this after.

Thanks you guys

The driver files consist of binary libraries (32-bit), if I'm not mistaken. They - on their side - depend on other libraries. Those are old and cannot be found on the new Ubuntu system. Hence copying the driver files should not be of any help (you can extract them from the installation archive/package without a hassle).

I asked Canon to recompile their drivers for newer systems (after all they got the source and all it takes is to issue a 'make' command on a newer system), but their reply basically translated into "we don't care". No reply from the Ubuntu staff, so far...

Cheers,
                  LC

---

### Post by K-Jtan on 2011-06-16
> **_-LC-_ said:**
> The driver files consist of binary libraries (32-bit), if I'm not mistaken. They - on their side - depend on other libraries. Those are old and cannot be found on the new Ubuntu system. Hence copying the driver files should not be of any help (you can extract them from the installation archive/package without a hassle).

I asked Canon to recompile their drivers for newer systems (after all they got the source and all it takes is to issue a 'make' command on a newer system), but their reply basically translated into "we don't care". No reply from the Ubuntu staff, so far...

Cheers,
                  LC

Sad to hear this, I always thought Canon was a great company with good support for Linux OS.

Thanks you for the information
K-Jtan

---

### Post by PapaGary on 2011-06-16
This worked for me:

[http://www.ubuntubuzz.com/2011/06/download-install-canon-printer-driver.html](http://www.ubuntubuzz.com/2011/06/download-install-canon-printer-driver.html)

---

