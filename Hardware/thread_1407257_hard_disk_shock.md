---
title: "hard disk shock"
date: 2010-02-15
forum: Hardware
---

### Post by Adnanius on 2010-02-15
Morning, 
my wireless keyboard fell from about 1 meter on my xps1330 laptop, it hit just above the hdd. my ubuntu system was running, and went on running normally, until I decided to restart the system. 
It then started giving block reading errors; and couldn't start GUI. text mode does start.  
Same thing with my windows partition: block reading errors, and windows not starting.  
Good news is that everything else than hdd seems to be working correctly: it's now booted from ubuntu cd.
I can access my data from both ext3 and ntfs partitions.   
I'm running a fsck now, asking for "force rewrite". 
Can I hope this will correct errors? 
how to know if the hdd is still physically normal? i.e. would a format-reinstallation takes everything back to normal?
I need to get this fixed asap, I've got a lot of work to do...

---

### Post by hessiess on 2010-02-15
Replace the drive ASAP, shocking a running HDD will cause the head to crash, which damages ether the head, the surface of the disk or both. With some luck, your data may still be OK, try to find an external adapter for the drive (2.5" enclosure or 2.5" -> 3.5" converter)

---

### Post by Adnanius on 2010-02-15
thank you for the quick answer, 
I copied all important data using the ubuntu live cd.
after that, I made fsck rewrite error blocks, and upon restart,the laptop couldn't detect the hdd anymore. 
when I try to boot from disk, it says no disk detected, and I can't see the hdd via live cd anymore.

means the hdd passed away? any way to diagnose?

---

### Post by Adnanius on 2010-02-16
well, seems that I'm going to buy a new hdd. 
I decided to install ubuntu on my external hdd in the meantime. 
It was an ntfs unique partition. 
I created 1 swap and 1 ext3 partitions at the end of the hdd. 
I installed via live cd, root and grub on the ext3 partition. 

Problem: when I try to 'boot from usb', I get a black screen with a blinking cursor, and nothing happens... help...

---

### Post by viper250 on 2010-02-16
good choice if you do an install to an external drive you have the capability of having a live spare of your system.
and if your system can boot from usb you have a method retrieving your data
and running it in an emergency

---

### Post by Megafag on 2010-02-16
> **Adnanius said:**
> the laptop couldn't detect the hdd anymore. 


Try setting everything in your bios to default. in the past that has helped me magically detect hard drives.

---

### Post by Adnanius on 2010-02-16
Well it seems that grub isn't loading. Choosing 'boot from USB disk drive' ends with a black screen and a blinking command...

---

### Post by efflandt on 2010-02-17
During installation to the external drive, did you pay attention to the **Advanced** button at the summary just before actual installation proceeds.  If you do not know what I am asking about, you may have installed grub in the default location in the mbr of your (inaccessible) main hard drive instead of the mbr of the external drive.

---

### Post by Adnanius on 2010-02-17
Well actually yes I did ask for grub to be on my external ext3 (see my previous post)

I did the error of installing grub on root drive, and not in the MBR. Now it's working flawlessly! 
Many thanks...

---

