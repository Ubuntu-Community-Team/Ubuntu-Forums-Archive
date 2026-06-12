---
title: "Natty Narwhal vs Broadcom 4322AG"
date: 2011-09-22
forum: Hardware
---

### Post by Horizonz on 2011-09-22
Hello all! I'm proud to say that about a week ago I'm officially a new linux user. :) Natty Narwhal and the new Unity desktop really impressed me, and I've been spreading the word around to my IT buddies. ;)

Anyway! My tower's PSU died on me yesterday, so I've resorted to using the ol' laptop. In an effort to improve the performance of the laptop, I promptly installed my newly discoved wonder-OS; Ubuntu! Said laptop is a HP TouchSmart tx2-1025dx and uses a Broadcom 4322AG wireless networking card. Said laptop also does _not_ have a standard ethernet port, which did a nice job of screwing over my driver search. >.<

Long story short, I'm brand new to linux and only know just enough to find my way to the terminal. Ubuntu was unable to load drivers for my wireless card automatically, and without internet on the laptop, I'm unable to use the built-in driver searching software. 

I did my research first, and found a driver download packaged in a .tar.gz file, but being totally unfamiliar with linux I'm unsure how exactly to use this driver file. As far as I can gather, .tar.gz files are compressed files (somewhat like .rar or .zip files?). The driver file is currently residing on the windows side of the laptop under the directory: C:\Users\Horizonz\Downloads\hybrid-portsrc_x86_32-v5_100_82_38.tar.gz

Can anyone help me with a step-by-step noob guide to sorting out this driver problem in Ubuntu 11.04 with no internet access?

Thanks!
-Hori

---

### Post by coffeecat on 2011-09-23
Welcome to the forum.

First, are you sure you don't have an ethernet port? I have an HP Mini which at first I thought came without an ethernet, but closer examination revealed a carefully-hidden one under a removable dust cover that needs long fingernails or an implement to prise off. And Hewlett-Packard list a gigabit ethernet card in their specification for that model:

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01634461&cc=us&dlc=en&lc=en](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01634461&cc=us&dlc=en&lc=en)

Have a look here:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

According to that, your Broadcom 4322AG requires the STA driver. There are instructions for installing the STA driver from files on the live CD here:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA_-_No_Internet_access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA_-_No_Internet_access)

---

### Post by Horizonz on 2011-09-23
Thank you very much, coffeecat! :) I'll give this a go and see how it all turns out. Have a great day!

---

