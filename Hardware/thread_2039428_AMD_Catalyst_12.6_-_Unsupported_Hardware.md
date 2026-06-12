---
title: "AMD Catalyst 12.6 - Unsupported Hardware?"
date: 2012-08-08
forum: Hardware
---

### Post by irishetalon007 on 2012-08-08
Jockey only goes up to catalyst 12.4 in ubuntu 12.04, but I'm trying to install catalyst 12.6 manually as described in the following pages from AMD's unofficial wiki:

[http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide)

Please don't suggest a fix already listed on either of those pages as I've already tried them all....

PC Specs:
Pavilion G6-1D46Dx
CPU (APU) : AMD A6-3420m w/ RADEON HD 6520g graphics

Command outputs:

```
fglrxinfo
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  139 (ATIFGLEXTENSION)
  Minor opcode of failed request:  66 ()
  Serial number of failed request:  13
  Current serial number in output stream:  13

```

```

amdconfig
amdconfig: No supported adapters detected

```

strangely, when i do

```
amdcccle
```

and then click the information panel, it correctly displays my hardware:
AMD Radeon HD 6520G

If anyone can at least point me to someone who knows about my hardware configuration and can help me out, I'd obviously be a very happy camper :)

Thanks for your time!

---

### Post by QIII on 2012-08-08
It looks like you do not have the driver compiled into the kernel.

Would you post the results of 

```
lspci -nnk | grep -iA2 vga
```

---

### Post by irishetalon007 on 2012-08-14
it seems that since the last time I tried this, fglrx-updates has been updated to a newer driver and is working very well!

I'll mark this as solved and reopen it if necessary in the future...

---

