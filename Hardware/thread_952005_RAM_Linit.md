---
title: "RAM Linit"
date: 2008-10-18
forum: Hardware
---

### Post by cjwallace on 2008-10-18
Hi guys.

I have installed Ubuntu on a HP DL360 G4 and the server has 5GB of RAM. This server is used for Zabbix.

When i look at the server i only see 3.6GB of RAM. Is there something i need to edit for Ubuntu to see this extra RAM. Under windows you have to edit the boot.ini is there something like that under Ubuntu?

Please note i am soooooo new to linux but am loving Ubuntu so far and am looking forward to getting to grips with it. I sort feel like i did when i started with windows 13 years ago.

Many thanks for any help you can give

Craig

---

### Post by phidia on 2008-10-18
This has been dicussed here (and I wish I could find the exact thread I want).

Basically for 32bit systems you need to install the server kernel to get recognition of memeory >4GB.

This line though > I have installed Ubuntu on a HP DL360 G4
makes me wonder if you are saying this is a PPC processor?

If it is then I'm not sure what support for over 4GB is like on that.
You could install the 64 bit version.

---

### Post by wakojakop on 2008-10-18
> **cjwallace said:**
> 
When i look at the server i only see 3.6GB of RAM. Is there something i need to edit for Ubuntu to see this extra RAM. Under windows you have to edit the boot.ini is there something like that under Ubuntu?


The motherboard can only take 3.6gb
had problem with it too

---

### Post by cariboo on 2008-10-18
I just had a look at the HP web site about your server, it says the computer can support up to 12 GB of PC2-3200 DDR2 400 SDRAM so. If you are using the 32bit desktop kernel the most you are going to see is 3.6Gb, to be able to use the full amount of ram you need to install the server kernel. To install the server kernel go to System-->Administration-->Synaptic Package Manager and search for linux-image-2.6.xx-x-server, I'm not sure which version of Ubuntu you are using so I can't be more specific.

Jim

---

### Post by garydauphin on 2009-01-16
How did you get the RAID controller to work properly with Ubuntu.

I have tried everything, and it installs fine, but when I reboot from Hard drive, it sits with a flashing cursor.

---

### Post by electrogeist on 2009-01-18
> **phidia said:**
> G4 -- This line though makes me wonder if you are saying this is a PPC processor?

This is not a PowerPC.  But like Apple, HP/Compaq uses G# to enumerate generation.  Also, what Apple calls a G4 are actually quite a number of different PPC chip model #s.
 
 
> **garydauphin said:**
> How did you get the RAID controller to work properly with Ubuntu.

I have tried everything, and it installs fine, but when I reboot from Hard drive, it sits with a flashing cursor.

You can figure out what RAID controller it uses and figure out what the appropriate kernel driver is (google can help), then see if your kernel was compiled with support for it.  Like the higher memory limit, the ubuntu server kernel might include better support for a wider range of RAID controllers.  This would probably be best discussed in another thread

---

### Post by sergueik on 2009-01-18
Actually all 32-bit systems have limit of supporting only 3.6GB of Ram. It is pretty universal and applies to Windows and Unix. Both Windows and Unix systems have some sort of patches to make this work, however, it is not recommended by anybody who is familiar with PC architecture. Normally, if you want large Ram support, you would use 64-bit OS. Actually, similar applies to a well-known 2GB single file size limit. I am not a doctor or anythiog, but from what I understand, this has to do with IO capacity of the 32-bit data exchange (or something like that). Use of any patches to "split the traffic" might result in reliability and performance issues. Read more on that kernel update, if it is written for 64-bit hardware and you have that hardware -  you are game, if not, you will not gain much, but might loose in performance of less demanding applications. Be careful, do not do it if you do not need it.

---

### Post by electrogeist on 2009-01-18
Intel rolled out PAE in the Pentium 3 era to work around the 32-bit addressable 4GB limit.  There will be a slight performance hit.  I do not know of any reliability issues with it.  In linux anyway.  Windows never supported PAE except in some server editions...I do remember hearing that it would have played havoc with many common windows drivers because the way they were coded.

BTW I have a dual P3 board here that supports a whopping 8GB PC133, in dual channel even, also has 64-bit PCI on multiple buses and u/160 scsi - and to put the icing on the cake - even an AGP slot!!  Tyan FTW!

---

