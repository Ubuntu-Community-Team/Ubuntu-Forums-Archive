---
title: "Wireless card not working on ASUS UX30"
date: 2010-04-30
forum: Hardware
---

### Post by trym.dahl@online.no on 2010-04-30
Hi
I just kicked W7 and are happy for that, but setting up my UX30 with Ubuntu Ult. I have run Into some problems.  First I am new to Linux, but not to computers in general.
The problem is that the wireless card does not work. Tried upgrading to the new 10 release from 9.10 to get the kernel 2.6.32-21-generic that is supposed to work with the driver RaLink 3091 Wireless, that is installed.

Does anyone know how to solve this ? If so I would very much apreciate a step by step guide to this solution.

---

### Post by zukk on 2010-05-10
I just purchased ux30 and, as usual, kicked Win from it. 
I've installed Lucid Lynx Netbook edition and found my wireless card unable to scan for any network.
I've tried to switch to wicd but this hadn't help. After some hours of googling and reading forums I found solution.

So, that worked for me:
Find some wired connection and go [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)
Download [RT3090PCIe]("http://www.ralinktech.com/license_us.php?n=2&p=0&t=U0wyRnpjMlYwY3k4eU1ERXdMekF5THpJekwyUnZkMjVzYjJGa09Ea3pOalE1TlRBd09DNWllakk5UFQxU1ZETXdPVEJmVEdsdWRYaFRWRUZmVmpJdU15NHhMalJmTWpBeE1EQXlNakl1ZEdGeUM%3D") driver, unpack it to some directory.
It was /home/Downloads/RT3090_LinuxSTA_V2.3.1.4_20100222 for me
Enter this directory in terminal and run

> sudo make
> sudo make install

In my case it mumbled something about gcc, so i typed:
> sudo aptitude install gcc

After restart wireless interface appeared in network manager, and now I connected using it.

Hope this will help someone else.

---

### Post by aspergerian on 2010-05-15
Neither desktop nor netbook versions of 10.04 generate working wireless on my HP Mini Mi 1000, which originally was loaded with Linux and which runs 8.04 Ubuntu quite well.

---

