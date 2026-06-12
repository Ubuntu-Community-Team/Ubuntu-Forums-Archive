---
title: "MCE Remote stops working randomly"
date: 2007-11-27
forum: Hardware &amp; Laptops
---

### Post by NTolerance on 2007-11-27
I've got an MCE remote (Philips version, uses lirc_mceusb2 driver) running on Gutsy which has been upgraded from Feisty.  The remote worked great in Feisty but after upgrading to Gutsy it will randomly stop working.  irw gives not output when the remote stops working.  I can get it going again by completely rebooting the machine.  

```
sudo /etc/init.d/lirc restart
``` will not get the remote working after it fails, only a reboot will.  Does anyone know would could have changed to cause this problem?

---

### Post by NTolerance on 2007-11-30
bump

---

### Post by JAKEOTR on 2008-02-25
I'm having the same problem...anybody have a possibility here? Is it OK to apt-get upgrade the Mythbuntu machines (always heard once its working dont mess with it) and might this solve the problem?

Thanks

---

