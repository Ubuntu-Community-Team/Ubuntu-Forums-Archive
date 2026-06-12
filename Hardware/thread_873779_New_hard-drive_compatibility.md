---
title: "New hard-drive compatibility"
date: 2008-07-29
forum: Hardware
---

### Post by research800 on 2008-07-29
Hi,

I've a Inspiron 6000 laptop with XP installed. Recently, my harddrive crashed and am looking to buy a new internal harddrive. I also want to install and use only Ubuntu on the new harddrive. I'm fairly new to Linux world, so any help would be appreciated.

* Can Ubuntu automatically detect the new harddrive?
* Is there any information on Ubuntu hardware compatibilty? I will be buying a ATA-6 or Ultra ATA100 type harddrive.
* Can I just install the harddrive and use Ubuntu install CD or is there anything I need to do before installing Ubuntu?
* I want to connect my laptop (after installing Ubuntu) to TV using S-video, what software would I need for that?
* Does Ubuntu support wireless connectivity? I've a ProIntel wireless card.

Thanks

---

### Post by tamoneya on 2008-07-29
1. Yes but you will need to partition it as you do with every new harddrive on windows or linux
2. As far as harddrives go they will all be compatible with linux.  Just go with whatever is best for your laptop and budget.
3.  Thats all you need.  Pop in the new harddrive then the CD in the drive and boot it up.  You may have to enter the BIOS to tell it to boot from the CD drive.
4.  That is fine.  There really isnt anything extra you need.  Just setup a multiple screens with System -> applications -> screen resolution.
5. Yes.  Intel should be detected and installed automatically.  You shouldnt have to do anything.

---

### Post by research800 on 2008-07-29
Thanks

Does Ubuntu installation CD support harddrive partitioning or should I first do it with some partitioning tool (i've GParted) and then install Ubuntu?

I'm planning to buy a harddrive for 160GB, could someone give an idea on what would be an ideal way to partition the disk and what partitions are needed?
I understand, partitioning is dependent on how I intend to use the laptop. If I could get some general guidelines around it, that'll be very helpful. I plan to use this laptop for general usage, mostly I will be running Apache, Oracle or MySQL servers.

---

### Post by tamoneya on 2008-07-29
> **research800 said:**
> Thanks

Does Ubuntu installation CD support harddrive partitioning or should I first do it with some partitioning tool (i've GParted) and then install Ubuntu?

I'm planning to buy a harddrive for 160GB, could someone give an idea on what would be an ideal way to partition the disk and what partitions are needed?
I understand, partitioning is dependent on how I intend to use the laptop. If I could get some general guidelines around it, that'll be very helpful. I plan to use this laptop for general usage, mostly I will be running Apache, Oracle or MySQL servers.

If you install with the liveCD you can tell it to automatically partition the entire disk for you.  This is probably what you want (assuming you dont want to put MS on it).

---

### Post by evets25 on 2008-07-29
Yes, the partitioner is integrated right in to the ubuntu installer, and is retty easy to use. If you want to do the partitioning beforehand, you can always run gparted from the live CD, and do the partitioning that way, and then just tell the ubuntu installer "use this partition for this and that partition for that." 

As far as hard drive compatibility goes, there's shouldn't be a problem. A hard drive is a hard drive, and it doesn't need an OS-specific driver to work. If you think about it, this makes perfect sense, since the OS resides on the hard drive, so if there is some driver that is specific to the OS that needs to be loaded in order to read from the hard drive, where exactly would it get loaded from? The hard drive? :)

---

