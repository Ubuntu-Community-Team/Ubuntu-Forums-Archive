---
title: "Moving from Windows XP"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by Benne90 on 2009-11-06
Okay so now I have downloaded ubuntu-9.10-netbook-remix-i386.iso, what should I think about before I change from my current operating system Windows Tiny XP to Ubuntu Netbook, on my [Dell Latitude C400]("http://support.euro.dell.com/support/downloads/driverslist.aspx?c=se&l=sv&s=gen&ServiceTag=7020G0J&SystemID=LAT_PNT_P3_C400&os=WW1&osl=se&catid=&impid=").

The laptop came with its own external CD-ROM drive and floppy drive, I need to install drivers for these two, how would this be done once I have ubuntu installed?

In addition, I have two printers I want to install the drivers for, and a logitech webcam.

Most important is that this computer does not come with a built-in wireless, so I must also install the drivers for my external USB wireless adapter ([D-link DWA 160]("http://www.dlink.com/products/?pid=656")).

Then it is also the whole procedure of reformating the computer and installing ubuntu from a usb stick, what must I change in Bios to make this possible?

Thank you very much if someone takes the time to answer my questions
Sincerely,
Benjamin

---

### Post by witeshark17 on 2009-11-06
Are you planning a format and fresh install?

---

### Post by Benne90 on 2009-11-07
In the end yes, but before I even get near putting it on the computer I want to know how much work will be involved in order to get the computer working.

---

### Post by Mark Phelps on 2009-11-07
You won't be able to use any of the current drivers you have because they're all for MS Windows, not for Linux.

Unless you can boot the machine from a LiveCD, it's going to be really hard to tell how well Ubuntu will detect and install the proper drivers.

---

### Post by XPM on 2009-11-07
> **Benne90 said:**
> Okay so now I have downloaded ubuntu-9.10-netbook-remix-i386.iso, what should I think about before I change from my current operating system Windows Tiny XP to Ubuntu Netbook, on my [Dell Latitude C400]("http://support.euro.dell.com/support/downloads/driverslist.aspx?c=se&l=sv&s=gen&ServiceTag=7020G0J&SystemID=LAT_PNT_P3_C400&os=WW1&osl=se&catid=&impid=").

The laptop came with its own external CD-ROM drive and floppy drive, I need to install drivers for these two, how would this be done once I have ubuntu installed?

In addition, I have two printers I want to install the drivers for, and a logitech webcam.

Most important is that this computer does not come with a built-in wireless, so I must also install the drivers for my external USB wireless adapter ([D-link DWA 160]("http://www.dlink.com/products/?pid=656")).

Then it is also the whole procedure of reformating the computer and installing ubuntu from a usb stick, what must I change in Bios to make this possible?

Thank you very much if someone takes the time to answer my questions
Sincerely,
Benjamin

[http://ubuntuforums.org/showthread.php?t=1308563&highlight=dwa-160](http://ubuntuforums.org/showthread.php?t=1308563&highlight=dwa-160)

Didn't work for me. Never has. It worked in 9.04 by compiling and loading modules manually...but seriously. Who wants to do that all the time? It gave me errors when trying to load auto.
In fact, I wont do anything until it is supported officially.
Nor was it in 8.10

Edit: And blacklisting the USB didn't work either as mention in the other thread:

[http://ubuntuforums.org/showthread.php?t=960642&highlight=dwa](http://ubuntuforums.org/showthread.php?t=960642&highlight=dwa)

---

### Post by Benne90 on 2009-11-08
Geesh well then I guess Ubuntu is out of the question for me :( I guess I'll just do a clean install of XP and hope the laptop works smother. Lately I have been getting lots of blue screens, and since bluescreens never are worth the time they take to debug I am just going to reinstall the laptop. 
Cheers Guys thanks for all the help!

---

### Post by heyted on 2009-12-05
> **Benne90 said:**
> Okay so now I have downloaded ubuntu-9.10-netbook-remix-i386.iso, what should I think about before I change from my current operating system Windows Tiny XP to Ubuntu Netbook, on my [Dell Latitude C400]("http://support.euro.dell.com/support/downloads/driverslist.aspx?c=se&l=sv&s=gen&ServiceTag=7020G0J&SystemID=LAT_PNT_P3_C400&os=WW1&osl=se&catid=&impid=").

I am using Ubuntu 9.10 (not the netbook remix) on my Dell Latitude C400 with no problems.

> **Benne90 said:**
> The laptop came with its own external CD-ROM drive and floppy drive, I need to install drivers for these two, how would this be done once I have ubuntu installed?

If you are using the original Dell external cd and floppy drives, you have nothing to worry about.  The nonproprietary drivers will be installed automatically during the instillation.  

> **Benne90 said:**
> Most important is that this computer does not come with a built-in wireless, so I must also install the drivers for my external USB wireless adapter ([D-link DWA 160]("http://www.dlink.com/products/?pid=656")).

I bought my C400 without an internal wireless mini pci card, and I later bought one and installed it.  There are easy step-by-step instructions specifically for the C400 on the Dell website describing how to do it.  The internal card will most likely get better reception than a USB adapter.

> **Benne90 said:**
> Then it is also the whole procedure of reformating the computer and installing ubuntu from a usb stick, what must I change in Bios to make this possible?

Reformatting is done automatically during the instillation.  The whole install process was easy with no problems.  I burned the iso to a cd instead of using a USB stick, but changing the boot device order is easy by pressing F2 while the C400 is first booting.

---

