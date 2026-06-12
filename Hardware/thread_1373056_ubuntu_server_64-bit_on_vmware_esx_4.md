---
title: "ubuntu server 64-bit on vmware esx 4"
date: 2010-01-05
forum: Hardware
---

### Post by jpgeerets on 2010-01-05
hi

i have an esx4 machine with a intel xeon E5520.

on this machine i want to install ubuntu 64-bit.
during install i get the next error:
> This kernel requires an x86-64-bit CPU, but only detected an i686 CPU.
Unable to boot - please use a kernel appropriate for your CPU.

on the same esx machine, i run several w2k3-64 bits.
as far as i can see on the intel-site, the processor is 64-bit.
[http://ark.intel.com/Product.aspx?id=40200](http://ark.intel.com/Product.aspx?id=40200)

anyone any idea?

Thanks in advanced!

Jean-Paul

---

### Post by jpgeerets on 2010-01-06
solved...

need to change bios settings...

---

### Post by squ1rr3l on 2010-02-04
I'm having the same issue.  What BIOS settings did you change to fix it?  VM BIOS settings or Host BIOS settings?

---

### Post by jpgeerets on 2010-02-04
i changed the host bios.
some virtual settings

---

