---
title: "How to disable swap on live CD"
date: 2008-11-21
forum: General Help
---

### Post by Matthai on 2008-11-21
Ubuntu live CD uses swap partitoon of the host system. How to disable this on a remastered CD?

---

### Post by taurus on 2008-11-21
Applications -> Accessories -> Terminal
```
sudo swapoff /dev/sda5 (or whatever the partition your swap is)
```

---

### Post by ibuclaw on 2008-11-21
```
sudo swapoff -a
```

Will turn off **all** swap devices. So you will only run on RAM and cache.

Regards
Iain

---

### Post by Matthai on 2008-11-21
No.

The problem is, that swap was already mounted.

If you are doing forensic examination of the machine, you already touched swap partition and destroyed the evidence...

so how to prevent swap to be mounted at boot time with live cd?

---

### Post by ibuclaw on 2008-11-21
According to the Knoppix Cheat Codes, the word **noswap** as a boot parameter should do what you expect.

Though I can't guarantee this, as I have never tried it.

Regards
Iain

---

### Post by bodhi.zazen on 2008-11-21
> **Matthai said:**
> No.

The problem is, that swap was already mounted.

If you are doing forensic examination of the machine, you already touched swap partition and destroyed the evidence...

so how to prevent swap to be mounted at boot time with live cd?

Can not do this with a standard ubuntu disk. Use something more specialized for forensics.

There are numerous options, here is but one

[http://www.caine-live.net/en/page2/page2.html](http://www.caine-live.net/en/page2/page2.html)

---

### Post by ibuclaw on 2008-11-21
Top 10 Security/Forensic LiveCDs:
[http://www.darknet.org.uk/2006/03/10-best-security-live-cd-distros-pen-test-forensics-recovery/](http://www.darknet.org.uk/2006/03/10-best-security-live-cd-distros-pen-test-forensics-recovery/)

Regards
Iain

---

### Post by Matthai on 2008-11-22
I know this special CD's. But I want to remaster Ubuntu CD... :)

---

