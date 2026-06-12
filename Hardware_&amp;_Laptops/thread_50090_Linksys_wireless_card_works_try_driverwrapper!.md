---
title: "Linksys wireless card works: try driverwrapper!"
date: 2005-07-19
forum: Hardware &amp; Laptops
---

### Post by Dukeman330 on 2005-07-19
Hi folks.  I've got a linksys WPC54G ver.2 wireless card, and like many others, I've been banging my head aganst a wall trying to get the friggin thing to work.  After days of playing around with ndiswrapper and such, I caught a thread where someone mentioned, in passing, a tool called "driverloader".
"Driverloader," I said, "what could this be?"
And lo, after a bit of searching, I quickly found this:
[http://www.linuxant.com/driverloader/wlan/full/downloads-ubuntu-x86.php](http://www.linuxant.com/driverloader/wlan/full/downloads-ubuntu-x86.php)
I downloaded the deb, installed it with:
sudo dpkg -i driverloader_2.28_k2.6.10_5_386_ubuntu_i386.deb.zip
then followed the instructions the program gave regarding setting a password and connecting to a configuration screen.  I booted up my browser and used their nifty web-based interface to load in the lstdns driver from the linksys website.  And voila!  I suddenly had a fully-functional wireless card.  I almost cried tears of joy.

So, in summary:** try driverloader**!  Good luck!  If you have any questions regarding my rather painless procedure, let me know.

~Dukeman

---

### Post by moberry on 2005-07-19
That program is at this point superior to ndiswrapper. It costs money though. $19.95 for a permanent license.

---

### Post by Dukeman330 on 2005-07-19
Really?  It didn't ask me for any money... well, if it ever does, seems like a small price to pay for completly hassle-free wireless.   :grin:

---

### Post by jhmoore719 on 2005-07-22
I just downloaded it, and then went to the linuxant store.  

[https://www.linuxant.com/store/](https://www.linuxant.com/store/)

It looks like you get a 30 day free trial or you can get the unlimited license for $19.95.

I've been researching this, off and on, for about 2 weeks now without much success.   ](*,) 

jack

---

### Post by jdkron on 2005-07-23
I went to the website and clicked on the link but nothing happened.

Is there some special way to download it?

---

### Post by jhmoore719 on 2005-07-24
This is the link to follow to download driverloader for ubuntu.

[http://www.linuxant.com/driverloader/wlan/full/downloads-ubuntu-x86.php](http://www.linuxant.com/driverloader/wlan/full/downloads-ubuntu-x86.php)

This is the link to follow to get the license

[https://www.linuxant.com/store/](https://www.linuxant.com/store/)

BTW:  I have not loaded the linuxant driverloader or its drivers.  I've been trying to get ndiswrapper to work without success as yet.   ](*,)  I've just heard that a couple of people have gotten their wpc54g v2 wireless card working with driverload.  So do not take this as an endorsement.

---

