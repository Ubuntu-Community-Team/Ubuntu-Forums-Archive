---
title: "Espon XP-302 Printer Drivers"
date: 2014-02-06
forum: Hardware
---

### Post by Turkoglue on 2014-02-06
Hello everyone :) First of all im sorry for my " bad " english.
Today i install Linux Ubuntu 12.04 LTS and everything working fine, but my printer ( Espon XP-302 ) doesn't. I add him to System -> Printing. But if i wan't to printing or scaning nothing happend. I think i install linux printing drivers, but still nothing happens ( i new in this software, so i need some help :) )

---

### Post by howefield on 2014-02-06
Where did you get the printer driver from, there is a driver for that printer available on the Epson web site.

```
http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=17708&DSCCHK=9541f8150f52a1d9322c70c3e7320e7ae64b1f07

```
Sometimes adding the printer via localhost:631 works better. In a web browser type in the address bar localhost:631 and press enter.

---

### Post by Turkoglue on 2014-02-06
Thank you for your advice and help.

But i still have some questions: In this yours link i install ( epson-inkjet-printer-201201w_1.0.0-1lsb3.2_i386.deb ), but that i have to do with *epson-inkjet-printer-201201w-1.0.0-1lsb3.2.i486.rpm* , *epson-inkjet-printer-201201w-1.0.0-1lsb3.2.x86_64.rpm* and *epson-inkjet-printer-201201w-1.0.0-1lsb3.2.src.rpm* files ?

---

### Post by howefield on 2014-02-06
It is a .deb file that you need, so it would the the deb file ending in i386.deb if you are running 32 bit Ubuntu or if you are running the 64 bit version of Ubuntu you would need the deb file ending in amd64.deb

If you are not sure whether you have 32 bit or 64 bit, open a terminal and type the following

```
uname -a
```

press enter and post the output back here.

---

### Post by Turkoglue on 2014-02-06
I install this file with .deb and ubuntu software center show that drivers is install

Terminal show this: 
turk@turk-G41MT-S2:~$ uname -a
Linux turk-G41MT-S2 3.8.0-35-generic #52~precise1-Ubuntu SMP Thu Jan 30 17:27:28 UTC 2014 i686 i686 i386 GNU/Linux

And my printer(scaner) have showing that his didn't see that he pluged in to PC, so i think i have still this problem.

---

### Post by howefield on 2014-02-06
How are you connecting to the printer ?

Is it via a USB cable or have you set it up wirelessly ?

---

### Post by Turkoglue on 2014-02-06
Yes, i have USB cable. 
And my printer(scaner) have showing that his didn't see that he pluged in to PC, so i think i have still this problem ( maybe driver ? ).

---

### Post by Turkoglue on 2014-02-06
I think i go back tu Windows, becouse this is crazy thing... :) If printer working fine - this operation system would be best :)

---

