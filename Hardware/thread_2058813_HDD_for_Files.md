---
title: "HDD for Files"
date: 2012-09-16
forum: Hardware
---

### Post by bower4311 on 2012-09-16
I want to buy a HDD for files, I'm thinking 3TB. I'm running 12.04LTS and I read somewhere that WD green's don't work well with Linux, but that may be running the operating system. Will I run into any problems with one of these hard drives just for files? Any suggestions for best hard drive to buy?

Thanks

---

### Post by jerrrys on 2012-09-16
Best to ask the manufacturer if linux is supported.

 [http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=hdd+compatibility&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=hdd+compatibility&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

---

### Post by oldfred on 2012-09-16
I have not heard of any issues.

Some wanting better RAID systems want black, but those are faster drives.

With 3TB you will have to use gpt partitioning. MBR only goes to 2.2TB.

---

### Post by steeldriver on 2012-09-16
The Greens have a known issue with power management - specifically the idle timer that controls head parking - which can cause unusually high load cycle counts. This is one of the reasons they are not recommended for RAID applications, I don't know how much (if at all) it affects non-RAID, non-system applications - although fwiw I am running a pair of the 2TB EARS drives in RAID1 after using idle3tools to disable the timer. 

[http://support.wdc.com/product/download.asp?groupid=609&sid=113](http://support.wdc.com/product/download.asp?groupid=609&sid=113)

[http://www.storagereview.com/how_to_stop_excessive_load_cycles_on_the_western_digital_2tb_caviar_green_wd20ears_with_wdidle3](http://www.storagereview.com/how_to_stop_excessive_load_cycles_on_the_western_digital_2tb_caviar_green_wd20ears_with_wdidle3)

Bottom line - I think they'd be fine as non-RAID data drives, if you're at all concerned you can monitor the load cycle count via smartctl and take steps if the counts are getting out of hand

---

### Post by Jagoly on 2012-09-18
On top of that, you can have some problems with advanced format (4k as opposed to 512b sectors) which can cause the drive to be very slow if you don't set it up right at first.

Even though they do get a lot of bad publicity, I usually buy Seagate drives. They don't use any non standard technology that can be a pain.

---

### Post by arsenic23 on 2012-09-18
Honestly I have had some terrible problem in both linux and windows with the greens over the last 16 months.  By terrible problems I mean I'm having an unacceptably high number of them fail completely.  

I don't recommend them for anything right now.

---

