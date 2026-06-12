---
title: "SGPIO / SAS Backplane Utilities? Marvell SAS + Supermicro"
date: 2010-07-31
forum: Hardware
---

### Post by pneumatic on 2010-07-31
I've purchased some Supermicro 36-bay SC847A-R1400LPB chassis and a bunch of their AOC-SASLP-MV8 (Marvell 6480, mvsas) SAS controllers.

Everything seems to be functioning (I can see drives that are plugged in) except for the major aspect of managing the drives.  How do I hotplug and eject?  How do I blink an indicator on a drive so that I know which drive is bad?  Is there some SGPIO utility available to do this?

Is this within the capabilities of Linux?  I'd certainly love to avoid installing Windows on these things...

---

### Post by pneumatic on 2010-08-01
[http://rhn.redhat.com/errata/RHEA-2009-0212.html](http://rhn.redhat.com/errata/RHEA-2009-0212.html)

This is what I am looking for, I think.

Do I need to install Redhat?

---

### Post by afspear on 2011-03-18
Did you ever find anything out about this?  I'd like to install this as well but we are using debian

---

### Post by candlerb on 2012-09-25
> **pneumatic said:**
> [http://rhn.redhat.com/errata/RHEA-2009-0212.html](http://rhn.redhat.com/errata/RHEA-2009-0212.html)

This is what I am looking for, I think.

Do I need to install Redhat?

```

apt-cache search sgpio
apt-get install ledmon
man ledmon

```

For ubuntu 12.04 anyway.

---

