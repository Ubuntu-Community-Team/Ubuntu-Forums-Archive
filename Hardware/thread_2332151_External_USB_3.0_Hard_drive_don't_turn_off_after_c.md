---
title: "External USB 3.0 Hard drive don't turn off after computer shutdown Ubuntu 16.04"
date: 2016-07-28
forum: Hardware
---

### Post by lemanitou on 2016-07-28
I dual boot Windows 10 & Ubuntu 16.04

My external Seagate USB  3.0 HDD won't turn off when I shutdown my computer under ubuntu, but  everything works fine with win10.

  My external HDD is always connected and always in the same port.
  
On shutdown in Ubuntu, drive stays powered on. 
On shutdown in  Windows, drive shuts down. 
Funny thing, when I put Ubuntu to sleep the  drive turn off.

  
I have played with the BIOS, turned off the charging feature. I tried  udisksctl and hdparm commands with no luck. My first idea was to make  linux run a script at shutdown to manually turn it off, but it look like  I can only spin it down.


  The only thing I didn't try is to enable the XHCI Hand-off option in my BIOS.


  My new computer have a ASUS H170 (LGA 1151) Pro Gaming motherboard.

---

### Post by lemanitou on 2016-07-31
Ok, I have a temporary solution for my problem. I enabled ErP in my BIOS

> ErP Support determines whether to let the system consume less than 1W of power in S5 (shutdown) state. When the setting is enabled, the following four functions will become unavailable: PME Event Wake Up, Power On By Mouse, Power On By Keyboard, and Wake On LAN. 

It works... but It isn't the right solution in my opinion...

---

