---
title: "HP Laptop Won't boot 9.04"
date: 2009-09-13
forum: Installation &amp; Upgrades
---

### Post by mocadedhed on 2009-09-13
Hi, I've got a problem with my laptop not booting after "successful installation" message of 9.04. I've installed from md5sum correct ISO image, done a memory check and used the installation CD to verify the integrity of the drive.
 
When I turn the system on I'm getting a Black Screen with a flashing cursor.
Seems like the MBR file is gone?
 
Does anyone have a link to a process for installing a new boot record? or a step by step on any alternatives?
 
Thanks for any help. This is all after I've given over 100% of the disk to the Ubuntu installation - not trying to dual boot or anything like that.
 
Compaq/HP Presario V4000

---

### Post by mocadedhed on 2009-09-14
So, after several attempts trying to get this install to work I've finally succeeded  - which sounds a lot harder than it actually was.
After two installations that were "successful" according to Ubuntu installation verbiage Failed I elected to install a third time and did not install a boot loader. The system wouldn't boot, however i performed a 4th installation and it worked!!

The error i was receiving earlier was "Unable to start the Installer" - you need to check your disk or possibly your CD (try buring your CD at a slower speed).

After researching why that might be I almost concluded that I had some kind of defective hard drive. However, in the process of trying to get the failed installations to boot I installed grub 2 which never seemed to register with my system.

Regardless, i installed from the LiveCD one more time and it worked.

I know this isn't helpful to any of you guys that know what you're doing, but I'm happy to report I have a good clean install of Ubuntu 9.04 for my wife to work off of and I'm all set.

---

