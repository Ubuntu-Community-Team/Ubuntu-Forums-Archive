---
title: "Step by Step Instructions for an Idiot to get his Epson XP-247 working"
date: 2017-02-17
forum: Hardware
---

### Post by ukneil on 2017-02-17
Okay I am hoping someone can help me by providing step by Step Instructions for an Idiot to get his Epson XP-247 working.... Here's hoping!

---

### Post by yancek on 2017-02-17
Generally, the process involves opening System Settings and clicking the Printer icon and following the steps.  Have you done that and what were the results?

---

### Post by ukneil on 2017-02-18
Yes it recognizes the printer on my USB port. When it goes searching for drivers there is not one for the Epson XP-247. I visited this page:
[http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=53634&DSCCHK=3cf26785012f7834dd7fa0384c94f366f846fdd9](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=53634&DSCCHK=3cf26785012f7834dd7fa0384c94f366f846fdd9)

And downloaded some files that are now sitting in my downloads folder in a folder called
epson-inkjet-printer-escpr-1.6.11

That is as far as I have got.

---

### Post by slickymaster on 2017-02-18
*Thread moved to **Hardware**.*

---

### Post by yancek on 2017-02-18
> 
And downloaded some files that are now sitting in my downloads folder in a folder called
epson-inkjet-printer-escpr-1.6.11

There are options on that page to download rpm, deb or tar.gz files.  The one you want is the one with the .deb extension.  If you have a 32bit machine, you need the one with i386 in it.   If you have a 64bit machine, you need the one with the amd64 in it.  If you have the correct driver in the Downloads directory, double click the file and you should be asked how you want to install, usually it will be the Software Center so just proceed from there.

If you have the rpm or tar.gz file, delete it and download the correct one.

---

### Post by verymadpip on 2017-02-18
Hi there.
I have an XP 332 which was a little bit tricky initially.
This thread was really helpful:
[https://ubuntuforums.org/showthread.php?t=2261230](https://ubuntuforums.org/showthread.php?t=2261230)

It seems to be a case of installing drivers & then running the printer setup utility.
Good luck.

---

### Post by maglin2 on 2017-02-18
There is a version of escpr in the repositories - 'printer-driver-escpr' if I recall correctly. I would be inclined to try that first - it worked for me (on an XP-425).

PS - You won't find it in the software centre, but you should if you install synaptic and then search that.

---

### Post by ukneil on 2017-02-18
It works! 
Thanks you for the help. Very much appreciated.

In summary I:
Went to this page:
[http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=53634&DSCCHK=3cf26785012f7834dd7fa0384c94f366f846fdd9](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=53634&DSCCHK=3cf26785012f7834dd7fa0384c94f366f846fdd9)
 I am using 64 bit so I downloaded this....
[COLOR=#333333][FONT=Tahoma]epson-inkjet-printer-escpr_1.6.11-1lsb3.2_amd64.deb     
[/FONT][/COLOR]to my downloads folder
 Clicked on it and it installed from the Software Centre

Job Done! Thanks again.

---

### Post by oldrocker99 on 2017-02-18
Great that your problem is fixed. Please use the Thread Tools to mark this thread as [SOLVED].

---

