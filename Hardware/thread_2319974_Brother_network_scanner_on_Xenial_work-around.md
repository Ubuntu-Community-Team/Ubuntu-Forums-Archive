---
title: "Brother network scanner on Xenial work-around"
date: 2016-04-09
forum: Hardware
---

### Post by vidtek on 2016-04-09
I'm happy with most stuff on xenial, but have had a few glitches.

The Brother MFC driver installs well and wireless printing works straight off 
after using the Brother script  "linux-brprinter-installer-2.0.0-1" from their website.
Wireless network scanning installed but xsane stubbornly refused to work.

I found a work-around by copying the 

/usr/lib64/sane 

directory to 

/usr/lib/

My mfc is the MFC-885CW

Cheers, Tony.

---

### Post by zinzolinn on 2016-08-25
Worked for me on Xubuntu 16.04 64bits and printer Brother DCP-195C. 
Thanks a lot!
Nicolas
:)

---

