---
title: "Ferrari 3400 ndiswrapper issue"
date: 2006-07-08
forum: Hardware &amp; Laptops
---

### Post by idkim on 2006-07-08
Hi, I'm trying to get my Ferrari 3400 to recognize the Broadcom WLan. I have obtained multiple 64bit drivers since I'm running the Breezy Badger 64 bit. One of the driver is from this forum

[http://ubuntuforums.org/attachment.php?attachmentid=186](http://ubuntuforums.org/attachment.php?attachmentid=186)

the problem is when I install this driver by using ndiswrapper -i command I get this following message
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2

there is a driver that does not return any of that message but both drivers output the exact same result as listed below

modprobe ndiswrapper
<no output for both driver>
iwconfig
<driver from the forum does confirm the existance of eth0, my wireless port>
<other driver does not even display this>
when I scan for possible AP by using the following command

iwlist wlan0 scan

<both drivers output this
 wlan0 Interface doesn't support scanning.>

Any help will be very appreciated.

Dan.

---

### Post by idkim on 2006-07-08
Ok...another problem

I just went to the Network setting under Systems,.

my eth0 used to be visible up there before I messed around with ndiswrapper but now it's not even up there.

what is going on.... :(

---

