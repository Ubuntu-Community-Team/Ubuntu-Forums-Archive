---
title: "SATA RAID0 not getting picked up..."
date: 2005-05-01
forum: Hardware &amp; Laptops
---

### Post by Zensunni on 2005-05-01
When setting up raid, I usually go to the firmware on my motherboard and make a raid array. Then I install windows and it sees my raid array as one hard drive. I guess ubuntu is too smart, however, for whenever I set the array up in the motherboard settings, the install program still sees it as two drives. What even worse is when I try to partition both drives, I get the grub error 2 when my computer starts up again for the second part of the install.

I'm just new to linux, so if this is a stupid question, forgive me.

---

### Post by heimo on 2005-05-01
Not a stupid question at all. Most motherboard raids are not pure hardware raid controllers. Those still need software (drivers) to work and use CPU to do some of the work. I'd suggest using Linux software raid or pure hardware raid.

---

### Post by Zensunni on 2005-05-01
Alright, I'm pretty sure my setup is software. Otherwise ubuntu either would just see one drive, or wouldn't be able to communicate with the drives at all.

Does this mean that I need to create a linux partition on the raid with a boot disk first, then install ubuntu on that partition, or do I need to change the setup configuration...or neither?

How do I go about setting up a linux software raid array? I'll look on google, but if you have a good direct answer, that'd be awesome.

---

### Post by heimo on 2005-05-02
Actually I've never setup Linux software raid. Linux Software-Raid-HOWTO should give some advice, man mdadm is also one place to start. I'm not sure if raid0 can be used as a boot device, but raid1 can.

[http://www.tldp.org/HOWTO/Software-RAID-HOWTO.html](http://www.tldp.org/HOWTO/Software-RAID-HOWTO.html)
[http://www.tldp.org/HOWTO/HOWTO-INDEX/howtos.html](http://www.tldp.org/HOWTO/HOWTO-INDEX/howtos.html)

---

### Post by alastair on 2005-05-02
Unless things have improved, forget about motherboard/BIOS level SATA RAID with Linux. Windows has a special driver to see the SATA RAID - Linux doesn't. So Linux sees 2 disks. You /can/ still do RAID, but have to get to the OS (mdadm etc.).

---

