---
title: "82573L Gigabit Ethernet not working"
date: 2007-09-11
forum: Hardware &amp; Laptops
---

### Post by Chillbilly on 2007-09-11
Hey all

I have a Samsung X60 Laptop and my Ethernet is not working under Ubuntu feisty.

$ lspci
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller (rev 01)

sudo pppoeconf
it said : no Ethernet detected

I guess there is the right driver needed?

With google i found someone with a X60 and Debian but he made his on kernel:
“After recompiling the kernel with PCI express support it worked”

I never recompiled a kernel myself.
My question: can someone point me to a good solution for this problem?

Thanks for any help

---

### Post by Chillbilly on 2007-09-12
Any help would be much appreciated, thanks :)

---

### Post by jalvani on 2007-10-22
I'm rocking the same problem. The only workaround I've found on my Lenovo T60 is to reboot, and the OS will find and use a generic driver. Unfortunately, this is not only inelegant, but a pain in the *** as well.

If I can track down more information, I'll pass it on to you.

---

### Post by Truxpin on 2008-06-06
I feel like I got here too late, but I had the same problem with the little device and it went away after a reboot. 
In fact I'm running 8.04 and with a previous version this very same IBM T60p ran UBUNTU and found the ethernet at the first shot. 

Hope this could help some other unlucky 82573L chipset user.

---

### Post by nouri on 2008-06-09
A better workaround is to:

  $ sudo depmod -r e1000
  $ sudo depmod e1000

---

