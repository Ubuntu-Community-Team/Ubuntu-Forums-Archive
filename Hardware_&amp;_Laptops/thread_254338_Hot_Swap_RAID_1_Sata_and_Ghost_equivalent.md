---
title: "Hot Swap RAID 1 Sata and Ghost equivalent"
date: 2006-09-09
forum: Hardware &amp; Laptops
---

### Post by merly on 2006-09-09
Hello, 

I want to build a computer that will be a Ubuntu computer with hot swap RAID 1 using SATA 2 (3Gb/s) hard disk drives, but would appreciate some guidance. 

1. Can I just get two SATA hard disk drives, install them in caddies (for example a SATA 2 version of [http://myahead.com/go/look/product.show_product?v_id=4734](http://myahead.com/go/look/product.show_product?v_id=4734)) and then connect the SATA cables directly from the caddies to the hard disk drive controller on the motherboard, leave the motherboard's built-in RAID functionality switched off (which I gather is fake RAID anyway), and then install Ubuntu using Linux's Multiple Device (md) feature which is installed with Ubuntu to create an md based RAID system? I gather md based RAID is meant to be the best way of doing RAID on Ubuntu? Does the Ubuntu installer automatically detect the two drives and ask if I want to create a RAID set up with them e.g. RAID 1 i.e. is the md side of things a part of the Ubuntu installer? Also, I don't know if the end result would be hot swappable (what would happen to Ubuntu while booted if I power down one of the two mirrored drives with a view to replacing it? The Ubuntu Wiki page on RAID ([https://wiki.ubuntu.com/Raid](https://wiki.ubuntu.com/Raid)) recommends using md which is why I'm asking how to go about this. Or is the only way to get hot swap RAID by using a real hardware RAID controller (e.g. 3Ware) to connect to the two disk drive caddies?

2. Is there an open source equivalent of Symantec's Norton Ghost that would work in a RAID environment like the one I outline above?

3. I gather the latest kernel of Ubuntu has an internal firewall (IP_tables). Could you please advise if IP_tables configuration is a part of the Ubuntu installer or can IP_tables be easily configured via the graphical user interface somewhere or is it purely a command line thing?

Regards.

---

