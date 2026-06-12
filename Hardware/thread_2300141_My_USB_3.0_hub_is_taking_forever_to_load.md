---
title: "My USB 3.0 hub is taking forever to load"
date: 2015-10-23
forum: Hardware
---

### Post by Tristan_Cormier on 2015-10-23
I am using a Gaming 9 AC motherboard from MSI and have been experiencing some serious problems with the back I/O area of the board for a short while now.
First off, the bluetooth & Wi-Fi module that came with the board was either broken or my motherboard shorted during its installation. Now another problem has been happening for a few months and I believe it may be caused by my latest BIOS update: My USB 3.0 hub on the back I/O area is not accepting any device, whatever I try. Also, it is not recognized on Windows 10 and it would tell me I had an unrecognized device connected. Now, my PC will take about 30 seconds to get out of the BIOS loading screen (freezes on 9C or 99) and then it will take another 30-60 seconds for Ubuntu to respond upon logging in, and everything will **** up and I will have to log out for things to function properly.

Is there any way for me to diagnose the issue and maybe even fix it?
Thanks in advance for any help.

---

### Post by Tristan_Cormier on 2015-10-23
Here's a paste with all the interesting lines I could retrieve from the system log file: [http://paste.ubuntu.com/12908623/](http://paste.ubuntu.com/12908623/)

---

### Post by Tristan_Cormier on 2015-10-26
Anybody, pl0x?

---

### Post by Vladlenin5000 on 2015-10-26
Has your mobo an AMD970 chipset? If so then it's a known issue with IOMMU. Here's the two steps solution:

1. Turn IOMMU off in BIOS/UEFI.
2. Edit grub and add "iommu=soft".

---

### Post by Tristan_Cormier on 2015-10-26
> **Vladlenin5000 said:**
> Has your mobo an AMD970 chipset? If so then it's a known issue with IOMMU. Here's the two steps solution:

1. Turn IOMMU off in BIOS/UEFI.
2. Edit grub and add "iommu=soft".

It is not an AMD970 chipset. It is Z97 GAMING 9 AC from MSI and let me tell you it is total ********. I don't know what to do about this crap.

---

### Post by Tristan_Cormier on 2015-10-27
I'm still having problems and seriously contemplating getting a RMA. Is there any way I could possibly disable the USB hubs?

---

### Post by Vladlenin5000 on 2015-10-27
It should be an option at BIOS/UEFI.

---

### Post by Tristan_Cormier on 2015-10-27
I have fixed my problem by using the secondary BIOS, which is using an older version. Even my long-thought-broken Bluetooth/WiFi module now works. Thanks for the help.

---

