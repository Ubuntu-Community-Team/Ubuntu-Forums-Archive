---
title: "regionset error trying to update DVD drive despite available resets"
date: 2019-08-05
forum: Hardware
---

### Post by adam-hardy on 2019-08-05
I've got a new PC where the DVD region is set to '4' and regionset gives me an error when trying to set it to '2' even though it says I have 4 vendor resets available.

  adam@gondolin:~$ sudo regionset /dev/sr0
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: SET
vendor resets available: 4
user controlled changes resets available: 4
drive plays discs from region(s): 4, mask=0xF7

Would you like to change the region setting of your drive? [y/n]:y
Enter the new region number for your drive [1..8]:2
New mask: 0xFFFFFFFD, correct? [y/n]:y
ERROR: Region code could not be set!
adam@gondolin:~$ 
  This is the info from the hardware with smartmontools:
  adam@gondolin:~$ sudo smartctl -i /dev/sr0
smartctl 6.6 2016-05-31 r4324 [x86_64-linux-4.15.0-54-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, [www.smartmontools.org]("http://www.smartmontools.org")

=== START OF INFORMATION SECTION ===
Vendor:               HL-DT-ST
Product:              DVD+-RW GA31N
Revision:             A102
User Capacity:        730,214,400 bytes [730 MB]
Logical block size:   2048 bytes
>> Terminate command early due to bad response to IEC mode page
A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.
adam@gondolin:~$ 
I figure that 'bad response' is just something to do with the fact that it's a DVD drive and not a normal hard drive.  

There's currently a CD in the drive - it won't accept a DVD and therefore regionset won't run with a DVD, but according to regionset docs, that should be irrelevant.


  This is Ubuntu 18.04 Bionic, from the server install where I then installed Xwfm4 on top, if that makes any difference. 

  
Is there some linux wizardry I can do? 

I just checked for a replacement drive and it's an internal DVD drive where the DVD button fits my PC case, so it has to be Streacom - but I've been unable to find any, so fixing it is my priority!

---

