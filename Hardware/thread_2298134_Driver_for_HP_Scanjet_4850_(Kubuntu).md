---
title: "Driver for HP Scanjet 4850 (Kubuntu)?"
date: 2015-10-09
forum: Hardware
---

### Post by Constantinopolitan on 2015-10-09
Dear Ubuntu experts,

I have an OLD HP Scanner I'd like to connect to my Kubuntu laptop, and I didn't find any driver for it (HP Scanjet 4850) on the HPLIP platform. I also had a look at SANE Genesys but couldn't find anything to download.
When asking the Konsole if maybe there is already some HP scanner visible, I got the following answer:

"constantinopolitana@Constantinopolitana:~$ apt-cache search hp scanner
aes2501-wy - userspace software for usb aes2501 fingerprint scanner
kipi-plugins - image manipulation/handling plugins for KIPI aware programs
php-net-portscan - Portscanner utilities
python-scapy - Packet generator/sniffer and network scanner/discovery
wapiti - web application vulnerability scanner
constantinopolitana@Constantinopolitana:~$ ^C"

Anyone would know what that means? 

Thanks a lot in advance for your support!

Best regards,

Eva

---

### Post by Ubunterrific on 2015-10-11
Had a bit of a dig. Assuming Scanjet 4850C works, then we're in business. [http://www.sane-project.org/sane-mfgs.html#Z-HEWLETT-PACKARD](http://www.sane-project.org/sane-mfgs.html#Z-HEWLETT-PACKARD)

Right, so it seems this piece of kit needs the **genesys** backend. So...following these instructions: [https://help.ubuntu.com/community/SANE%20-%20Installing%20a%20scanner%20that%20isn't%20auto-detected](https://help.ubuntu.com/community/SANE%20-%20Installing%20a%20scanner%20that%20isn't%20auto-detected)

You need to begin with step 2, and change the line that reads:
```

#example-backend 

```
to be
```
genesys
```

and the rest should be easy enough. Let me know how it goes :popcorn:

P.S. ```
apt-cache search hp scanner
``` won't return a package specifically for these drivers because they're very old and seem to already be in sane but with this 'genesys' backend?

---

### Post by Ubunterrific on 2015-10-11
Woops - also - Bear in mind that the limitation mentioned on the page says that
> resolution from 100 to 2400 supported, UTA not supported yet

---

