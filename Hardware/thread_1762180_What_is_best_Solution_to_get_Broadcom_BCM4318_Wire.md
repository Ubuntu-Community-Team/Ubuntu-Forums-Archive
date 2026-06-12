---
title: "What is best Solution to get Broadcom BCM4318 Wireless Working in Dell Latitude 110L"
date: 2011-05-18
forum: Hardware
---

### Post by gmannhtown on 2011-05-18
I am very new to working with Linux, but good with PC's in general. I have installed Ubuntu (Natty) 11.04 on 3 machines so far. Seems to work great overall. I have now installed it on a friends Dell Latitude 110L. All went well, Ethernet port works great for internet access, but wireless is doing nothing. I ran the "lspci" command in terminal and it shows the Broadcom Corporation BCM4318 wireless device, but I just cannot get it to work. As well, there are no wireless networks being detected. Tried manual set up wireless network, but still no go. I have tried hitting "Control + F2" to ensure wireless is on although nothing is lighting up to indicate either way. 

I am at a point where I am ready to use the NdisWrapper route, but this is clearly a very tedious and lengthy process. I would like to ensure there are no alternate suggestions before trying this.

I have found all kinds of threads to attempt resolve, tried a couple with no success and simply want to see if anyone can suggest one that is more likely to resolve this matter and offers ez to follow instructions. Any suggestions or referral to a useful thread would be greatly appreciated.

---

### Post by gmannhtown on 2011-05-19
Okay, so after some added research a good night's rest, I emailed myself a few links to try first thing this morning and the very first one I sent myself worked. The link is as follows:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20b43%20drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20b43%20drivers) 

Thanks.

---

### Post by shnutzer on 2011-05-19
As a BCM4311 user I can say that b43 driver mentioned here works well (tested on Puppy Linux and Ubuntu 9.10), but sometimes the speed gets down to 1MB/s and the LED doesn't work.

For some people (like me) ndiswrapper may be a better solution

Guide here: [http://ubuntuforums.org/showpost.php?p=10823641&postcount=2](http://ubuntuforums.org/showpost.php?p=10823641&postcount=2)

---

