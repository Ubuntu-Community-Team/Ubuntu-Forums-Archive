---
title: "Getting my laptop to see my RAM"
date: 2009-09-30
forum: Hardware
---

### Post by piperdown10 on 2009-09-30
I'm trying to get my Toshiba Satellite to recognize my 4GB RAM update I installed last week. I'm on a Toshiba Satellite a135-s4427. I put 4GB of RAM in it and Jaunty is only seeing 2.9. I understand that some of the physical memory is diverted for other uses but I figured it would be somewhere in the park of 512k+. I checked my BIOS and it's only showing 3096 and I can't change it. Is there a way to fix this? Did I waste $75 on a RAM upgrade that my comp will never see?

Thanks ahead of time. :)

---

### Post by Hamchan on 2009-09-30
Sounds like you installed 32 bit Ubuntu. Switch to 64 bit and you'll find your missing ram.

---

### Post by piperdown10 on 2009-09-30
I do have the 32bit version. However, I tried installing the 64bit version before and I got an error saying that I did not have a 64bit processor and that it could not install.

Also, I compiled a new kernel last night with PAE enable.

---

### Post by Yellow Pasque on 2009-09-30
> I checked my BIOS and it's only showing 3096 and I can't change it.
If the BIOS only recognizes/supports 3GB, then it doesn't matter what OS or kernel you use. Double-check the manufacturer's specifications on the amount of RAM supported. If 4GB or more is supported, then make sure you're using the latest BIOS.

---

### Post by lukeiamyourfather on 2009-09-30
> **Temüjin said:**
> If the BIOS only recognizes/supports 3GB, then it doesn't matter what OS or kernel you use. Double-check the manufacturer's specifications on the amount of RAM supported. If 4GB or more is supported, then make sure you're using the latest BIOS.

Good call. There's also usually an option in the BIOS for software and/or hardware memory hole or memory remapping. Those options will need to be enabled for the system to see all of the memory. Cheers!

---

