---
title: "Suspected hard drive problem. Help........"
date: 2011-09-10
forum: Hardware
---

### Post by JohneG on 2011-09-10
I tried to install Ubuntu onto my acer aspire one (it has a ssd). It was a fresh install having previous used an older version of ubuntu. I keep getting an error saying that it couldn't install to the drive and that there may be a problem with the hard drive. How do i check my hard drive for any problems? I am using puppy linux off of a usb drive at the moment. Is there anything i can throw into the terminal to figure out what's going on? Thanks

---

### Post by dabl on 2011-09-10
If puppy has smartmontools installed, then you could run the SMART test, but perhaps an easier approach would be to make a Parted Magic Live USB stick and then use the SMART tools on it:  [http://partedmagic.com/doku.php?id=creating_the_liveusb](http://partedmagic.com/doku.php?id=creating_the_liveusb)

---

