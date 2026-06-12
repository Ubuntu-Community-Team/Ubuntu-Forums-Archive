---
title: "Samsung ML 2251N Laser Printer over Network - Finally!"
date: 2007-02-27
forum: Hardware &amp; Laptops
---

### Post by actuary286 on 2007-02-27
After numerous attempts with various distros and releases of K/X/Ubuntu I finally got my Samsung 2251N printer connected over to Linux over my home network. If anyone else has a balky 2251N  or other networked Samsung laser/mfp I have documented my solution:

It took a while, but I finally got my Samsung ML 2251N working with Feisty over the network.  The [Ubuntu Community Documentation]("https://wiki.ubuntu.com/HardwareSupportComponentsPrinters/SamsungMl2250") only covers the ML 2250, which is the non-networked version, and recommends using the drivers on the CD included with the printer, but I couldn’t get it to work, I kept getting errors after the install when the setup application tried to open.

Googling around a bit I found posts on the Ubuntu forums that recommended downloading the [Unified Driver]("http://www.samsung.com/ca/support/productsupport/download/FileView.aspx?cttfileid=303122&amp;type=&amp;typecode=300500&amp;subtype=&amp;subtypecode=300501&amp;cmssubtypecode=&amp;model=ML-2251N&amp;filetype=DR&amp;language=") from Samsung and using it instead. I downloaded it and tried, but got the following error:

```
./Linux/install.sh: 1232: source: not found
```

Googling the error message led me to this [how-to by Scott Bronson]("http://news.u32.net/articles/2007/02/05/the-samsung-unified-linux-driver-installer-on-ubuntu") that explained some of the issues with the unified driver and shows how to fix them. One important note is that although the 2251N is not a MFP I still apt-get’d sane just to be safe.

Following the how-to, I let the set-up program look for network printers then used the provided Samsung PPD driver. But, when I tried printing a test page, but still no success.

Heading back to trusty Google I found this [message]("http://lists.freestandards.org/pipermail/printing-user-samsung/2005/001256.html") on the [Printing-user-samsung]("http://lists.freestandards.org/mailman/listinfo/printing-user-samsung") mail list. The first parts didn’t really apply to me since I use static ip addresses and had already installed the unified driver, but the last part is what I needed.

After deleting my existing printer entry out of the Samsung Unified Driver Utility, I opened up Firefox and the CUPS admin interface ([http://localhost:631]("http://localhost:631")) and clicked Add Printer. Here is how I got a working install:

[LIST=1]
[*]Give the printer a name and fill in the other blanks if you want (I skipped them) .Here is the important part, for the connection protocol leave it on “AppSocket/HP JetDirect”.Then enter the address: socket://ip_address:9100. The :9100 is important to get data headed out to the right port.

[*]For Make/Manufacturer select SAMSUNG then Samsung ML-2250 Series (SPL II) (en). This is the PPD file provided by Samsung with the Unified Driver and made available in [step 2 of Scott’s how-to]("http://news.u32.net/articles/2007/02/05/the-samsung-unified-linux-driver-installer-on-ubuntu"). Then click Add Printer.

[*]In the Set Printer Options screen that come up next you may want to switch the Page Size to US Letter from A4.

[*]To test the setup select the Printers tab and then Print Test Page under your new entry for the 2251N (remember the nameyou gave it?).
[/LIST]

With any luck, your printer should spool up and spit out a nice little CUPS test page. Hope this helps anyone out there trying to get a 2251N working under Linux.

*This is also my first how-to style post for Linux so please feel free to provide feedback. Thanks.*

---

### Post by Plecebo on 2007-04-13
Awesome, 

I have been trying to get this to work for a very long time and it was one of the PITA things that was keeping me from booting to linux more often then Windows. 

Great Howto, worked like a charm.

---

### Post by Trondok on 2007-06-02
I just installed the ML-2251N driver (downloaded from [www.samsung.com](www.samsung.com)) on Feisty by running the Samsung install script. The printer seems to be working just fine.

Got the same "source: not found" message, and fixed it by editing the install.sh file, changing the first line from "#! /bin/sh" to "#! /bin/bash".

-trond

---

