---
title: "dual boot vs wubi inside windows"
date: 2009-10-16
forum: Installation &amp; Upgrades
---

### Post by aspergerian on 2009-10-16
I have two small netbooks running Hardy Heron and am considering buying an Acer Aspire One 751h with XP (1) and want to dual boot since I'll be using Ubuntu most of the time. 

I've been reading numerous posts and get the impression that dual boot is not quite the same as Wubi Ubuntu running within Windows. 

I'll probably have a 160 gig HD to work with and would prefer ~60 gig in XP and ~100 gig in Ubuntu.  I would hope that some/many files could be accessed by XP and by Ubuntu. 

Is there an advantage to doing a dual boot by not using Wubi?  Does Wubi have size limitations for its Ubuntu directory and files? 

The 751h will come with Windows (or Vista) as the primary OS, so I'll be adding Ubuntu. 

Suggestions appreciated. 


1. Amazon offering of 751h
[http://www.amazon.com/Acer-Aspire-AO751h-1545-11-6-Inch-Netbook/dp/B002A6LN6C/ref=sr_1_1?ie=UTF8&s=electronics&qid=1255736393&sr=8-1](http://www.amazon.com/Acer-Aspire-AO751h-1545-11-6-Inch-Netbook/dp/B002A6LN6C/ref=sr_1_1?ie=UTF8&s=electronics&qid=1255736393&sr=8-1)

---

### Post by earthpigg on 2009-10-16
> Is there an advantage to doing a dual boot by not using Wubi? Does Wubi have size limitations for its Ubuntu directory and files?

off the top of my head:

1) Since a Wubi install resides on the Windows partition, it is subject to all the same inefficiencies as the Windows filesystem (NTFS). For starters, this means it will fragment and run slower over time (and running defrag in windows is the only way to fix this.).

2) That also means that malware or a windows virus can affect Ubuntu much easier than on a true dual boot. (even on a true dual boot, a virus that destroys the MBR can... still destroy the MBR. which is where GRUB lives.)

3) Since Ubuntu in Wubi is a Windows file, it is incredibly hard to later remove windows *without* removing Ubuntu as well.

---

### Post by garvinrick4 on 2009-10-16
Wubi is folder inside of Windows, pick your size.
Wubi boots from grubdos4 not from linux grub2 or legacy.
Wubi accepts all dos files  files/host/users/(your name)
drag and drop into Ubuntu.
Windows does not take linux files. You have to put linux files onto
say an external drive then when in windows copy to where you desire. Not a big deal. 

With live cd in hand you can get Wubi going in 12 minutes or so. 
Should always have important files on back up drive anyway.

If you want to test Alpha's or Beta and do daily downloads and you
get messed up just uninstall wubi in Windows. Reinstall with live cd in 12 minutes and do them daily upgrades aqain. Does not mess with Grub at all.
Download current .iso of Ubuntu to desktop, burn to 10 cent CD and off you go. About 699.2 meg is current file. Have a nice day.

---

### Post by aspergerian on 2009-10-17
earthpigg & garvinrick4, 

Thank you for replying. From what each of you has written, my long range preference will be to install a non-wubi dual boot, tho' first I may experiment with a wubi install to see how 9.04 likes the Acer 751h hardware.

---

### Post by earthpigg on 2009-10-17
> **aspergerian said:**
> earthpigg & garvinrick4, 

Thank you for replying. From what each of you has written, my long range preference will be to install a non-wubi dual boot, tho' first I may experiment with a wubi install to see how 9.04 likes the Acer 751h hardware.

that is exactly how it is designed to work!

good hunting.

---

### Post by klimtelfe on 2010-12-13
Hi, I have a wubi install which has been caused its second boot problem from just installing updates. This last time I didnt even try to install the grub updates. Any one have links to install a dual boot without wubi? I just managed to back up the files. The partitions are already present from the time I thought I was isntalling a regular dual boot.

---

### Post by presence1960 on 2010-12-13
From the developer of wubi, and this is a quote: 

Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

here is a link to the full interview: [http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)

---

### Post by Rubi1200 on 2010-12-14
> **klimtelfe said:**
> Hi, I have a wubi install which has been caused its second boot problem from just installing updates. This last time I didnt even try to install the grub updates. Any one have links to install a dual boot without wubi? I just managed to back up the files. The partitions are already present from the time I thought I was isntalling a regular dual boot.
For Wubi issues and solutions, see here:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by oldfred on 2010-12-14
This is a howto: thread on conversion from wubi to a full install.

HOWTO: migrate wubi install to partition - bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

