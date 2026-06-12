---
title: "Brightness-control just won't work on EEE 1001px"
date: 2010-08-17
forum: Hardware
---

### Post by DADAMAN on 2010-08-17
Hey,

some days ago I installed Lucid Lynx Netbook Edition on my EEE 1001px and so far it works fine. Way faster than Windows 7. :D

BUT, there's one thing bugging me so much. The brightness-control just won't work. I added the acpi_osi=Linux param to my burg config file and some of the FN-keys started working. 
Brightness adjustment worked so far, but when I turned down the brightness, some seconds later it jumped back to full brightness. 

So I found out about adding the acpi_backlight=vendor to my burg config. With that param brightness adjustment didn't work anymore. The display just flickered every time I tried raising or lowering the brightness.
Then I thought a bios update might do the trick, but wrong. Now the adjustment neither works with the param nor without it. :(

Is there anything I can do about that? I would really appreciate any help.  :D

---

### Post by DADAMAN on 2010-08-18
No ideas? :-(

I realized the flickering is worse when I work on battery. It just gets brighter/darker randomly. That's no fun. 
Would installing a driver or something maybe solve the problem?

---

### Post by NikoNZ on 2010-08-19
I had the same problem but the solution here: 

[http://ubuntuforums.org/showpost.php?p=9205249&postcount=2](http://ubuntuforums.org/showpost.php?p=9205249&postcount=2)

worked for me perfectly.

---

### Post by DADAMAN on 2010-08-19
> **NikoNZ said:**
> I had the same problem but the solution here: 

[http://ubuntuforums.org/showpost.php?p=9205249&postcount=2](http://ubuntuforums.org/showpost.php?p=9205249&postcount=2)

worked for me perfectly.

I already added that param to my burg conf and the fn keys work fine. Just brightness control doesn't work. :-(

---

