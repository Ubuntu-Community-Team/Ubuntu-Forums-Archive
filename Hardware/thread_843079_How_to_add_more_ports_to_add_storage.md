---
title: "How to add more ports to add storage?"
date: 2008-06-27
forum: Hardware
---

### Post by solexious on 2008-06-27
Hello,

Any one know a way to add more ports to a motherboard that I can connect either ide or sata hdds to? I have usb, pci available to me. Im looking to spend as lass as  can to get the ports.

So far the old things ive found have been very expensive raid cards, and as im using mdadm any way i don't need it...

Any thoughts or suggestions?

Sol

---

### Post by tamoneya on 2008-06-27
best to do it like this: [http://www.newegg.com/Product/Product.aspx?Item=N82E16816132007](http://www.newegg.com/Product/Product.aspx?Item=N82E16816132007).  

You want to be using the PCI slot since in terms of bandwidth PCI > SATA > USB so if you did sata through a USB port it would be limited by the speed of USB.

---

### Post by solexious on 2008-06-27
Thank you,

Being in the uk I can't order this, so what should i look out for? What in terms of drivers should i look for as must things arent tagged as linux compatible...

Sol

---

### Post by tamoneya on 2008-06-27
Honestly I just went to newegg and searched "pci sata" and this is the first one that showed up.  No magic to it.  As for linux compatibility the drivers are approaching 100% compatibility.  I dont know the chipsets for the sata cards off the top of my head so find one you like and then google "chipset_name linux" as long as you odnt see lots of posts like "Driver issues", "HEEELLLP my computer hates me" then you should be good.

---

