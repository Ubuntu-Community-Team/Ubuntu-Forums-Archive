---
title: "How To: Install an Epson Perfection Scan 3490"
date: 2010-02-14
forum: Hardware
---

### Post by AsusUL30 on 2010-02-14
Hello forum-visitors,
I'm quite new with Ubuntu, but have spent the last week in conquering this system so I don't have to switch to Windows XP or Windows 7.
I own an Asus UL30 Notebook, which is supported very well. Also my printer works fine. Although my scanner is not working so far.
When searching in the ubuntu forum, there should be a solution to use an Iscan plugin, which I downloaded in RPM-format. I tried to convert it with alien to a Deb package, but there it goes wrong. Alien doesn't convert it to Deb-packages, instead it creates two folders with a lock on it.
So i tried other thinks, like adding the epson, using this advise:
[http://ubuntuguide.org/wiki/Dapper#Install_the_correct_drivers:_Epson_Perfection_V200_Photo_example](http://ubuntuguide.org/wiki/Dapper#Install_the_correct_drivers:_Epson_Perfection_V200_Photo_example)
but also this  instruction doesn't work out for me (the machine# part does not work).
Is there an easy way to install this scanner?

---

### Post by IcarusR on 2010-02-14
Epson 3490 should work out of the box with xSane. Web site lists support as 'Good'.

Unless this is the Photo version, which just I noticed is unsupported.

---

### Post by AsusUL30 on 2010-02-14
Thanks for your response, it's indeed the Epson Perfection Scan 3490 Photo. According to the Epson website there is no difference between the 3490 and 3490 Photo. It's the same device. In lsusb my scanner is recognized, and in Sane as well, as you can see in this screendumps I made:

[http://www.websyte.nl/ubuntu/sane01.png](http://www.websyte.nl/ubuntu/sane01.png) 

Then I select this scanner, and the following message appears:

[http://www.websyte.nl/ubuntu/sane02.png](http://www.websyte.nl/ubuntu/sane02.png)

The Epson is supported, according to the Sane's website. The only question is, how do I get it working?

By the way1- thanks for your quick response
By the way2: [COLOR=Red]the reason i'm convinced there's no difference between the 3490 and 3490 Photo is because of he device number: 
Bus 002 Device 005: ID 04b8:0122 Seiko Epson Corp. Perfection 3590 scanner
And this device ID is exactly the same Sane's website is mentioning. So the software should support this device.[/COLOR]

---

### Post by IcarusR on 2010-02-14
Quite possible they have an entirely different chipsets one being supported & tother, yours, not. Epson do this.

Interesting that the device number is the same, yet on the 'git' version supported devices page it lists the 3490 photo as 'unsupported' yet lists backend etc.

> Perfection 3490 PHOTO 	USB 	0x04b8/0x0122 	Unsupported 	supported by the epkowa backend plus non-free interpreter 	epson2
(1.0.124) 	sane-epson2

Strange !!

---

### Post by AsusUL30 on 2010-02-14
Thanks again, indeed a mysterious thing. One should think there shouldn't be much differences between the devices, since the serialnumbers and devicenumbers are the same. But as I see it will be quite a queeste to get my scanner working under ubuntu. 
Somebody owns an Epson 3490 Photo?

---

### Post by Curbuntu on 2010-09-07
Did you ever discover a solution for this problem?  I'm encountering the same issue with an Epson Perfection 3590 Photo scanner.  XSANE can't see it in either Ubuntu 10.04.1 64-bit or Ubuntu 9.10 32-bit.  But the unit does show up in **lsusb** as **Bus 002 Device 026: ID 04b8:0122 Seiko Epson Corp. Perfection 3590 scanner**.

This has been a reliable, well-traveled veteran (I've taken it on many research trips), and I'd hate to have to install that other OS in a virtual machine to have to continue to use it.

---

### Post by makoto149 on 2010-10-06
So, where is the "How To" in this article. Sucky title. Please revise.

---

