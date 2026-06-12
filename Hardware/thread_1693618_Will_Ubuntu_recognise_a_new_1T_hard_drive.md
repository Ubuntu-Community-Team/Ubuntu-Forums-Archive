---
title: "Will Ubuntu recognise a new 1T hard drive?"
date: 2011-02-23
forum: Hardware
---

### Post by BravoDelta65 on 2011-02-23
I currently have 2 x 250gb hard drives in an old P4 dual core Dell Optiplex PC, which has 1gb ram (upgraded from original).

I've heard some stories on the net of people buying 1 Terra byte drives, but their system only recognises a fraction of that addressing range.

How do I find out if my system will be able to use the full capacity of the 1T drive before I purchase it?

---

### Post by cascade9 on 2011-02-23
They only time I know of where people have got HDDs and only been able to use part of the space is from the 128GB (137 'fake' GB) BIOS limit.

---

### Post by mastablasta on 2011-02-23
It's probably about western digital. some of their drives need to be aligned before you start adding data on them. after they are aligned everything works fine.
 
more here: [http://www.wdc.com/global/products/features/?id=7&language=1](http://www.wdc.com/global/products/features/?id=7&language=1)
here: [http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html?ca=dgr-lnxw074KB-Disksdth-LX](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html?ca=dgr-lnxw074KB-Disksdth-LX)
and here: [http://community.wdc.com/t5/Desktop/Problem-with-WD-Advanced-Format-drive-in-LINUX-WD15EARS/td-p/6395](http://community.wdc.com/t5/Desktop/Problem-with-WD-Advanced-Format-drive-in-LINUX-WD15EARS/td-p/6395)
 
+ here: [http://www.linuxconfig.org/linux-wd-ears-advanced-format](http://www.linuxconfig.org/linux-wd-ears-advanced-format)

---

### Post by cascade9 on 2011-02-23
Nah, alignment issues wont change the avaible space. 

BTW, its not just WD now, everyone is slowly moving to 4k sectors.

---

### Post by BravoDelta65 on 2011-02-23
So are you saying that I don't need to worry, and should just buy one?

I'm thinking of buying one of these:

[Samsung]("http://www.amazon.co.uk/Samsung-HD103SJ-internal-SATAII-7200RPM/dp/B004J35JZ0/ref=pd_rhf_p_t_2")

[Western Digital]("http://www.amazon.co.uk/dp/B003SLE8H4/ref=pe_81851_23932821_pe_epc_d1")

---

### Post by cascade9 on 2011-02-23
Depends. What model Optiplex?

---

### Post by BravoDelta65 on 2011-02-23
> **cascade9 said:**
> Depends. What model Optiplex?

It's an upgraded GX520. It has P4 dual core, 1GB ram, and my 2 Hitachi 250GB HDD's

---

### Post by cascade9 on 2011-02-23
Should be fine. Though the dell site does worry me (it has a '**Capacities up to 160GB**' warning on the spec page)- 

[http://www.dell.com/us/en/dfh/desktops/optix_gx520/pd.aspx?refid=optix_gx520&cs=22&s=dfh](http://www.dell.com/us/en/dfh/desktops/optix_gx520/pd.aspx?refid=optix_gx520&cs=22&s=dfh)

I did find places online that said that the GX520 will work with 1TB drives though. 

BTW, that WD drive is an 'advanced format' drive (4k sectors pretending to be 512b setors). If you use the 'wrong' tool to partition the drive, it will be a lot slower than it should be, and possibly shorten the lifespan of the drive.

---

### Post by BravoDelta65 on 2011-02-23
Thanks for your help Cascade9, much appreciated. I think I might just take the plunge and get the drive.

I thought the only restriction my be my OS (Ubuntu 10.10) and the system Bios of the PC, but I haven't heard any cautions regarding either of these.

---

