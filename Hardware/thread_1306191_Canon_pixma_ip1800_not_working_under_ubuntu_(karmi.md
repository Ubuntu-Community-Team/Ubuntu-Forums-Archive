---
title: "Canon pixma ip1800 not working under ubuntu (karmic)"
date: 2009-10-30
forum: Hardware
---

### Post by kio_http on 2009-10-30
How can I get my Canon pixma ip1800 inkjet printer to work in ubuntu. It works in OS X which also uses CUPS. Anyway to port the driver?

The printer looks like [IMG]http://www.metabilgisayar.com/alisveris/images/canon_pixma_ip1800.jpg[/IMG]

---

### Post by Shtrk on 2009-11-03
Have the same problem. It work in 9.04 fine, but when I upgrade to 9.10 and install driver I have before,it look like all is ok but printer is dead. Even queue shows that all is finished but nothing happing.

---

### Post by zerodalgorado on 2009-11-04
Hi, I've got exactly the same problem. And i get a "CUPS" error message when I try to print a test page : "client-error-document-format-not-supported".

---

### Post by kio_http on 2009-11-04
Thread bumped because its old and still has no useful replies

---

### Post by tantos on 2009-11-04
I've got the same problem...

---

### Post by SteveDee on 2009-11-05
I went thru this pain with Hardy, then Intrepid, but my iP1800 has continued to work after updrading from Jaunty to Karmic.

You might like to look at this thread if you haven't already done so: [http://ubuntuforums.org/showthread.php?t=850298&page=5&highlight=ip1800](http://ubuntuforums.org/showthread.php?t=850298&page=5&highlight=ip1800)

---

### Post by Maheriano on 2009-11-05
marked to view later

---

### Post by tantos on 2009-11-07
Solved by following instruction from :
[http://ubuntuforums.org/showthread.php?t=1305248](http://ubuntuforums.org/showthread.php?t=1305248)
then load ppd file using canonip1900.ppd

[http://tantos.web.id/blogs/how-to-karmic-koala-and-canon-pixma-ip1800-ip1900](http://tantos.web.id/blogs/how-to-karmic-koala-and-canon-pixma-ip1800-ip1900)

---

### Post by rafarian on 2009-11-08
that is working partialy

if you install this pronter as 1900 (or 2200 which is also working) you have no options for printer: no resolution, no quality options ;/

---

### Post by SteveDee on 2009-11-08
> **rafarian said:**
> that is working partialy

if you install this pronter as 1900 (or 2200 which is also working) you have no options for printer: no resolution, no quality options ;/

You should have a /etc/cups/ppd/iP1800-series.ppd file. This should contain sections like this:-

```
*OpenUI *CNQuality/Quality: PickOne
*DefaultCNQuality: 4
*CNQuality 2/High: "2"
*CNQuality 3/Normal: "3"
*CNQuality 4/Standard: "4"
*CNQuality 5/Economy: "5"
*CloseUI: *CNQuality
```

If not, backup your existing file, then copy chunks out of my attached file to yours and see what happens.

---

### Post by rafarian on 2009-11-11
it's working!

this is the code i copied from ip1800.ppd:

```
*OpenUI *Resolution/Output Resolution: PickOne
*DefaultResolution: 600
*Resolution 300/300 dpi: "<</HWResolution[300 300]>>setpagedevice"
*Resolution 600/600 dpi: "<</HWResolution[600 600]>>setpagedevice"
*Resolution 1200/1200 dpi: "<</HWResolution[1200 1200]>>setpagedevice"
*Resolution 2400/1200 dpi: "<</HWResolution[2400 1200]>>setpagedevice"
*Resolution 4800/1200 dpi: "<</HWResolution[4800 1200]>>setpagedevice"
*CloseUI: *Resolution

*OpenUI *CNQuality/Quality: PickOne
*DefaultCNQuality: 3
*CNQuality 2/High: "2"
*CNQuality 3/Normal: "3"
*CNQuality 4/Standard: "4"
*CNQuality 5/Economy: "5"
*CloseUI: *CNQuality

*OpenUI *CNGrayscale/Grayscale: Boolean
*DefaultCNGrayscale: False
*CNGrayscale True/Yes: True
*CNGrayscale False/No: False
*CloseUI: *CNGrayscale
```

ps. I tried this trick witch ip2200 driver and it didn't work - with ip1900 driver it's working perfectly :)

---

### Post by Nhorning on 2010-03-17
The previous worked for me.  However, I had to use the following command after I got an error. 

```
sudo chown root /usr/lib/cups/filter/pstocanonij
``` 

chown is a basic command but I'm sure there's plenty of newbs like me who don't know it.

---

### Post by GerryB on 2010-04-08
> **SteveDee said:**
> You should have a /etc/cups/ppd/iP1800-series.ppd file. This should contain sections like this:-

```
*OpenUI *CNQuality/Quality: PickOne
*DefaultCNQuality: 4
*CNQuality 2/High: "2"
*CNQuality 3/Normal: "3"
*CNQuality 4/Standard: "4"
*CNQuality 5/Economy: "5"
*CloseUI: *CNQuality
```

If not, backup your existing file, then copy chunks out of my attached file to yours and see what happens.

You can get the .ppd file from here:
[http://www.blogternals.com/2009/07/09/canon-ip1800-ubuntu/](http://www.blogternals.com/2009/07/09/canon-ip1800-ubuntu/)
Just take note of the folder where the file is downloaded - mine is called "Download". Extract the files there. Log out and back in as root.
Move the .ppd file to your /user/share/cups/drv folder (could be /cups/drivers, depending on the version). Log out and back in under your user name. Put the printer on - it should take care of everything from there, detecting the printer, searching for the driver on your hard drive. Wait till you see the message "Printer is online". Press "Test page". Should be ready to go.

---

