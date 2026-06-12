---
title: "Amilo a7645 and gemtek (Broadcom chip)"
date: 2005-10-10
forum: Hardware &amp; Laptops
---

### Post by konsa79 on 2005-10-10
Hi all,
i've a amilo a 7645 with WLAN Gemtek WMIB-160GW02EU20(LF) 

using ndiswrapper:

andrea@andrea:~$ ndiswrapper -l
Installed ndis drivers:
bcmwl5  driver present, hardware present

lspci :
0000:00:0b.0 Network controller: Broadcom Corporation: 
Unknown device 4318 (rev 02)

modprobe ndiswrapper and dmesg:

 [ 1673.156449] ndiswrapper version 1.1 loaded
 (preempt=no,smp=no) [ 1673.233310] ndiswrapper
 (check_nt_hdr:145): Windows driver is not 64-bit; bad
 magic: 010B
 [ 1673.233317] ndiswrapper (load_sys_files:456): unable to prepare 
 driver 'bcmwl5'
[ 1673.233786] ndiswrapper (ndiswrapper_load_driver:92): 
 loadndiswrapper failed (6); check system log for messages from 
 'loadndisdriver'


This is the orginal windows fujitsu driver, so i've dual boot disk and in windows all works well

[http://www.fujitsu-siemens.com/products/mobile/notebooks/amilo_a_7645.html](http://www.fujitsu-siemens.com/products/mobile/notebooks/amilo_a_7645.html)


this is the driver
Driver  - AMILO A1645  - AMILO A7645
 Filetyp: ZIP 		 Title: 		 WLAN Gemtek WMIB-160GW02EU20(LF)
 Date: 		 22.12.2004
 Size: 		 0,24 MB
Version: 		 3.100.46.0  
 Manufacturer: 		 Gemtek
Status: 		 Released for AMILO A7645
 



i've to wait the new kernel??????

:confused: 
regards

Andrea Consadori

---

### Post by mlomker on 2005-10-10
>  (check_nt_hdr:145): Windows driver is not 64-bit; bad


I assume that you are running amd64?  Are you sure that the Windows driver that you loaded is 64-bit (designed for 64-bit XP)?

---

### Post by konsa79 on 2005-10-10
is the only driver that exsist, in windows i use it on the same laptop without any problem.....

i take the driver from the fujitsu website, under driver of my laptop

---

### Post by mlomker on 2005-10-10
> is the only driver that exsist, in windows i use it on the same laptop without any problem.....

I believe that it works in Windows, but that isn't the only driver available and you didn't answer my questions.  Are you running Windows XP 64-bit?  Are you running amd64 Ubuntu?

---

### Post by konsa79 on 2005-10-10
windows is pre installed... is turion processor... how can i know if it's 32bit ore 64bit os?

so you're telling me that if've installer 64bit-ubuntu i've to search another driver... but where?

under the gemtek i cannot find it.. someone told me that from the next kernel the hardware will be supported (next ubuntu kernel, in debian 2.9.13 i think)

this is the gemtek page

[http://www.gemtek.com.tw/download.htm](http://www.gemtek.com.tw/download.htm)

but i cannot find fujitsu drive

---

### Post by mlomker on 2005-10-10
> how can i know if it's 32bit ore 64bit os?

If you go into the Control Panel, System it would say on that page if it is 64-bit.  If nothing is listed then it is the regular 32-bit Windows.  You usually have to ask for 64-bit in order to get it.

> under the gemtek i cannot find it.. someone told me that from the next kernel the hardware will be supported (next ubuntu kernel, in debian 2.9.13 i think)

I don't think so.  Broadcom has always refused to release linux drivers.

You could try a driver from [another laptop vendor]("http://www.ubuntuforums.org/showthread.php?t=52201"), it might work.

If you can't find one that works then you could always install 32-bit Ubuntu instead.

---

### Post by konsa79 on 2005-10-10
i just checked my xp
.. it 32bit version..... so if i use ubuntu 32bit i've lot of problem on laptop... so i've to find for gemtek 64bit driver..... mmm where i've to look for?

---

### Post by mlomker on 2005-10-10
> mmm where i've to look for?

You could start by calling Amilo's tech support.  If they don't have a driver then you'll have to experiment with drivers for other laptops, like in the link that I provided.

---

### Post by konsa79 on 2005-10-11
ok, with acer driver it works... now i'm testing wpa-supplicant...
this afternoon i've to make some debug cause last time i try use it , it crashed my os

---

