---
title: "Adding wireless PC card"
date: 2007-08-10
forum: Hardware &amp; Laptops
---

### Post by pethson on 2007-08-10
Hi!

I'm new to Ubuntu and Linux. And this might something everyone should know.
Anyhow, I installed Ubuntu 7.04 on my HP Pavilion zv5000 and it is realy nice.

Then I inserted my D-link DWL-650 wireless PC-card.
In windows I did got a message that I hade to install some drivers.

How do I get this to work in Ubuntu?

///Peter!:confused:

---

### Post by moore.bryan on 2007-08-10
*check out this other [thread]("http://ubuntuforums.org/showthread.php?t=450738"); it seems as though they got it working...*

---

### Post by ugm6hr on 2007-08-11
Indeed, ndiswrapper should work:
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_c-f/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_c-f/) (see entry 37)

This will help you get it going:
[https://help.ubuntu.com/community/WifiDocs/Device/RTL8180L](https://help.ubuntu.com/community/WifiDocs/Device/RTL8180L)
This is for edgy - so use ndiswrapper-utils-1.9 instead of -1.8, or compile the newest version yourself ([https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29) - but ignore the bits about the Broadcom device, and substitute your own drivers etc)

If ndisgtk misbehaves (which it does sometimes - very buggy), this will help do it from terminal:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-b30aaebf79b1393631b352f8f7a1acf5b17da38c](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-b30aaebf79b1393631b352f8f7a1acf5b17da38c)

Hope that lot provide the answer between them....  Any more questions - just ask (with details of what you've done).

---

