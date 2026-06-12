---
title: "100% CPU with USB printer"
date: 2005-08-10
forum: Hardware &amp; Laptops
---

### Post by marcw on 2005-08-10
I have a new, working 5.04 Athlon system.  I just purchased a Brother 420MFC mostly because Brother provides fairly good Linux support.  I had little trouble installing the printer using the Brother provided .deb install and driver files.  Everything works - printer, scanner, etc.  But then I noticed that my CPU (via GKrellm) was pegged at close to 100%.  At first I didn't realize why but then put 2+2 together and played around with my new Printer and some of it's settings.  Nothing I did to any of the settings or configurations made a difference until I unplugged the USB cable and rebooted.

Voila!!  My CPU immediatle returned to close to 0%!  If I then plugged the USB cable back in the CPU still stayed at 0%.  I then rebooted again this time with the USB cable plugged back in.  Once again my CPU went to 100%.  Unplugging it then makes no difference - it stays at 100%.

Anyone else see this?  Is this a Brother printer thing?  A USB thing?  A bug?  I'll take a closer look at my dmsg and other logs and see if I can post more info.  Thanks for any advice in the meantime.

---

### Post by marcw on 2005-08-10
Wow, this is weird...  No sooner had I rebooted my Hoary machine - with USB printer cable connected - than I saw that my CPU usage was back down to 0% i.e. normal.  Without having done one blessed thing to the machine.  I give up.  I have no idea why it behaved the way it did before nor do I understand why it appears to be working fine now.  Whatever...

---

