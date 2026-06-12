---
title: "[SOLVED] is sapphire ATI different to set up than regular ATI cards?"
date: 2007-08-16
forum: Hardware &amp; Laptops
---

### Post by A-Sylum on 2007-08-16
Is there a difference in setting up the driver for lets say a sapphire radeon 9250 than a radeon 9250?

do you have to use different drivers for them or which drivers do you use?
do they work better or worse in ubuntu than normal ATI?

thanks for the help!! :D

---

### Post by w4ett on 2007-08-16
> **A-Sylum said:**
> Is there a difference in setting up the driver for lets say a sapphire radeon 9250 than a radeon 9250?

do you have to use different drivers for them or which drivers do you use?
do they work better or worse in ubuntu than normal ATI?

thanks for the help!! :D

the 9200/9250 series cards are supported by the xorg-driver-ati only.....the different manufacturer SHOULD make little to no difference.  BTW, the proprietary fglrx driver only supports the 9500 and above cards

---

### Post by A-Sylum on 2007-08-16
Thank you so much. so that means i could use the drivers from ati.com for installation?

---

### Post by w4ett on 2007-08-16
> **A-Sylum said:**
> Thank you so much. so that means i could use the drivers from ati.com for installation?

Sorry, no...the driver for your card is already included in Ubuntu, and will (barriing unforeseen circumstances) install automatically.  The Binary Drivers at amd/ati.com will not work on your card.

See:  [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by A-Sylum on 2007-08-16
is it only ubuntu they dont work on? because i have found the drivers for 9250 and 9200 on ati.com. thanks!

---

### Post by w4ett on 2007-08-16
> **A-Sylum said:**
> is it only ubuntu they dont work on? because i have found the drivers for 9250 and 9200 on ati.com. thanks!

ATI is extremely bad in updating their drivers...the available binary drivers will not work on xorg 7.1 (on Edgy) and xorg 7.2 (feisty)....the Binary Legacy driver works only with Xfree86 (an older version of X, not available in Feisty Fawn).

---

### Post by A-Sylum on 2007-08-16
Thank you for all your help!

---

