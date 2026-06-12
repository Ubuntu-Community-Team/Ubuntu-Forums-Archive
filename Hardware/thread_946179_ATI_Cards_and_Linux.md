---
title: "ATI Cards and Linux"
date: 2008-10-13
forum: Hardware
---

### Post by Inxsible on 2008-10-13
I am planning on buying [this]("http://www.sonystyle.com/webapp/wcs/stores/servlet/CategoryDisplay?catalogId=10551&storeId=10151&langId=-1&categoryId=8198552921644564390&parentCategoryId=16154") laptop from Sony soon (probably by halloween). The only "problem" with it is that it only comes with an option of ATI cards. No nVidia available.

FW-190 has a ATI 3470 - 256 MB vRAM and 
FW-290 has a ATI 3650 - 512 MB vRAM chip.

Can anyone tell me if either of these cards work with the available Linux ATI drivers?


Also, if you know of other issues with Linux and Sony Vaio...please let me know.

---

### Post by Perfect Storm on 2008-10-13
moved to Hardware & laptops.

---

### Post by krazyd on 2008-10-13
These cards will work with the proprietary fglrx driver, but are not yet supported by the open source driver (only supports up to X1xxx Radeons). The fglrx driver works well for 3d, but exhibits tearing while watching video (no proper vsync).

AMD/ATI are currently in the process of releasing batches of information on their hardware/drivers to improve the open-source effort, which has already led to rapid improvements in hardware support. So open-source support for your card should be available in the future if you are patient :)

---

### Post by Inxsible on 2008-10-13
> **krazyd said:**
> These cards will work with the proprietary fglrx driver, but are not yet supported by the open source driver (only supports up to X1xxx Radeons). The fglrx driver works well for 3d, but exhibits tearing while watching video (no proper vsync).

AMD/ATI are currently in the process of releasing batches of information on their hardware/drivers to improve the open-source effort, which has already led to rapid improvements in hardware support. So open-source support for your card should be available in the future if you are patient :)
Not something that I wanted to hear.

But I am glad I know before buying it. I guess I will look at some other laptops which offer nVidia cards.
Thanks

---

