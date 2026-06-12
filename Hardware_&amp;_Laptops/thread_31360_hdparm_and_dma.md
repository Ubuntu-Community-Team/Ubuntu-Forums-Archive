---
title: "hdparm and dma"
date: 2005-05-02
forum: Hardware &amp; Laptops
---

### Post by Heretic09 on 2005-05-02
Trying to enable dma at boot by putting the following in the hdparm:

/dev/hda1 {
dma = on
}

gives error: unable to find file or directory /dev/hdc

which is odd becuase if I use hdparm -d1 /dev/hdc at the command prompt after it fully boots, it turns the dma on just fine.

if I use:
command_line {

    hdparm -d1 /dev/hdc 
}

I still get the same error during boot.

Anything i'm doing wrong?

---

### Post by ape on 2005-05-02
You aren't doing anything wrong.  The issue here is that the hdparm script in /etc/init.d is set to run before the script that detects and sets up your CD/DVD (as the case may be).  I believe that the hdparm script is set up as /etc/rcS.d/S07hdparm, whereas the script that loads the modules and such is in the S20 range.

---

### Post by mohaham on 2005-05-03
renaming it to /etc/rcS.d/S99hdparm 
should solve the problem...

---

