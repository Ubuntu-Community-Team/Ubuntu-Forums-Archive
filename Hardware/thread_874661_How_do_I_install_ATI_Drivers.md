---
title: "How do I install ATI Drivers"
date: 2008-07-30
forum: Hardware
---

### Post by higginsdj on 2008-07-30
The default Ubuntu 8.04.1 only offered a FireGL option for my HD3650.  I then downloaded and 'ran' the 8.7 ATI Catalyst file from ATI/AMD but when I log in again Catalyst reports a problem and only offers me 800x600.  Th eHardware drivers report that it is using the ATI drivers so I am at a loss as to what to do now (I am not LINUX literate....)

Cheers

David

---

### Post by alexforcefive on 2008-07-30
what is the error it gives you when you log in?

---

### Post by Vorian Grey on 2008-07-30
I always use Envy, found in the repositories. It has never failed me. It will download the correct driver and set everything up for you.

---

### Post by blacksea on 2008-07-30
> **Vorian Grey said:**
> I always use Envy, found in the repositories. It has never failed me. It will download the correct driver and set everything up for you.

that right
sudo apt-get install envyng-gtk
envyng -t

---

### Post by markbuntu on 2008-07-30
The repos are up to fglrx 8.501 which is the 8.6 driver, at least for amd64.

If you want the 8.7 driver, follow this guide, Method 2:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

---

### Post by higginsdj on 2008-07-31
Thanks guys.  Envy worked a charm :)

Cheers

David

---

