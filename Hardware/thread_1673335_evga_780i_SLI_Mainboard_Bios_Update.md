---
title: "evga 780i SLI Mainboard Bios Update"
date: 2011-01-22
forum: Hardware
---

### Post by blogmaniak on 2011-01-22
Hello Board ... happy 2011!
With start of this new year, I have run into an interesting issue, where my machine keep rebooting after certain time interval. I have seen the usual ACPI shutdown requested in my logs, for which the forumsphere has indicated that maybe a BIOS update might be needed.

Firstly, is there anyone else who is experiencing this same issue recently? Also, any suggestions around how I go about updating my bios, which currently is Phoenix - AwardBis V6.00PG? I have tried searching online, but haven't found anything specific with ubuntu 10.04 and SLI Motherboard BIOS update.

---

### Post by IcarusR on 2011-01-22
I have no experience of these mobos & don't know if bios upgrade will resolve your issue. But it is possible to flash bios.

Download the bios update from manufacturers website (asuming there is one available) & then follow something like the instructions here to create bootable cd to flash bios.

[http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html]("http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html")

---

### Post by blogmaniak on 2011-01-23
Thanks for the tip, that will help!
My main issue is that ubuntu 10.04 has randomly started rebooting. I don't know what to look for in my logs, to check why it is rebooting. It happens completely randomly. If any ideas please share!!

---

### Post by jeffery6803 on 2011-03-06
had the same problem with my board 780i happens when i have flash medium plugged in on system startup  when unplugged everything works fine  check if you have any flash drives plugged in

---

### Post by blogmaniak on 2011-03-06
> **jeffery6803 said:**
> had the same problem with my board 780i happens when i have flash medium plugged in on system startup  when unplugged everything works fine  check if you have any flash drives plugged in

That could be another reason why, but since this issue I tried to install windoze and system still keeps shutting down. I need to dig deeper and see if there is mobo/cpu temp issue. Argghhh such a pain to troubleshoot hwd issues.

---

### Post by cascade9 on 2011-03-06
> **blogmaniak said:**
> That could be another reason why, but since this issue I tried to install windoze and system still keeps shutting down. I need to dig deeper and see if there is mobo/cpu temp issue. Argghhh such a pain to troubleshoot hwd issues.

Its not that bad. If its restarting, just check the temps in BIOS. 
Its just as likely that there is a power supply/RAM problem as temps... 

As for the BIOS...evgas site sucketh most profound. 5 minutes, and I've already sworn off getting a evga board LOL. 

Seems that the only place I can find the info on the BIOS is he #$^#$ forum. 

P09 version- 

[http://www.evga.com/forums/tm.aspx?m=49810&mpage=1](http://www.evga.com/forums/tm.aspx?m=49810&mpage=1)

P10 version (not evga specific, its an nvidia reference BIOS)- 

[http://www.evga.com/forums/tm.aspx?m=133547](http://www.evga.com/forums/tm.aspx?m=133547)

BTW- 

> 6.00PG is not the version. the version will listed as P06. P07, P08, P09 or P10. mostly it added cpu support and some RAM fixes and delt with some issues with newer GPU's. if you look up the bios file they pretty much list what has changed, which is not much since P08

[http://www.evga.com/forums/tm.aspx?&m=133547&mpage=3](http://www.evga.com/forums/tm.aspx?&m=133547&mpage=3)

There might be newer BIOS than that, but I've already had enough. If defunct manufacturers like abit can do a decent BIOS downlaod page, why cant evga?

---

