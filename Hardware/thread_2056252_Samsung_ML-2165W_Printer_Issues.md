---
title: "Samsung ML-2165W Printer Issues"
date: 2012-09-11
forum: Hardware
---

### Post by mr.peeters@gmail.com on 2012-09-11
Hi, 

I bought myself a Samsung ML-2165W Printer, installed Samsung Unified Printer Driver (followed instructions on [http://ubuntuforums.org/showthread.php?t=341621](http://ubuntuforums.org/showthread.php?t=341621)). Now my computer seems to recognize the printer, but happily just says 'Document is Printing on ML-2160-Series' and a bit later 'Printing Completed'. In reality however, apart from starting to blink the green light a bit, my printer doesn't do a thing aaargh!

On weird thing maybe is that in my system settings / printers I have a printer called ML-2160-Series, but it mentions Samsung ML-2152WPS as the model...

Any help would be greatly appreciated!

Thanks a lot!
d.

Running Ubuntu 11.10, kernel 3.0.0-25-generic-pae, Gnome 3.2.1 on a Core i5 computer with 4GB memory.

---

### Post by dave30c on 2012-10-28
I see that no one replied to your posting.  Did you resolve the issue?  I've had the same problem with the same printer on my late 2011 MacBookPro (running Mt Lion).  Despite two lengthy calls to Sansung tech support, it will not print wirelessly.  We've gone through the set up routine multiple times which starts with a wired USB connection, then is supposed to connect to your WiFi network, but it's never printed while WiFi connected.  

I've probably going to return it to Newegg and get a different printer.  

Dave:mad:

---

### Post by Calixto Jorge on 2012-12-05
Try this driver: [http://www.samsung.com/br/support/model/ML-2165W/XAZ-downloads](http://www.samsung.com/br/support/model/ML-2165W/XAZ-downloads)

download for linux and ok. :)

---

### Post by omerub on 2013-03-11
> **Calixto Jorge said:**
> Try this driver: [http://www.samsung.com/br/support/model/ML-2165W/XAZ-downloads](http://www.samsung.com/br/support/model/ML-2165W/XAZ-downloads)

download for linux and ok. :)

thanks for samsung ml 2165w driver ;)

---

### Post by philpadova on 2013-09-05
**And then what to do?**

I tried the above on ubuntu 13.04 and then what follows :

I opened up the archive, cd into the new folder 
 
cd uld 

and then install

sudo ./install.sh

then I accepted the samsung agreement and then nothing new or better for my printer...

what else is to be done please?

---

### Post by antanasb on 2013-10-18
Go to [http://localhost:631](http://localhost:631) (I suppose you have CUPS installed) and add printer 'Samsung ML-2160 series'. Under Ubuntu 12.04 my ML-2165 works like a charm:)

---

### Post by Yahoé on 2013-10-31
On Trusty 64 (it should be the same with 13.10), I downloaded the driver (ULD_Linux_V1.00.06.tar.gz) from the Samsung site. It installed nicely and the printer works, connected through usb. I tried installing the smartpanel, it installed OK (libstdc++5 required) but doesn't launch.
The Printer settings utility installed nicely but I do not find anyway to invoke it
Samsung has a complete online manual : [http://downloadcenter.samsung.com/content/UM/201301/20130114180229138/EN/english/english/manual/start_advanced.htm](http://downloadcenter.samsung.com/content/UM/201301/20130114180229138/EN/english/english/manual/start_advanced.htm)

To further the tests, I also tried The Samsung Unified Linux Driver Repository [http://bchemnet.com/suldr/index.html](http://bchemnet.com/suldr/index.html) and installed the recommended 3.00.90 or 4.00.36 driver versions, but they did not work. As it reads on the site "Note that the 1.00.06 driver installer from Samsung seems to work fine,  and there is currently no seriously compelling reasons to use this  repository instead of Samsung's installer (unless you want an alternate  driver version or an easy install/uninstall system)."

I was able to update the firmware through a XP guest with ML2165W_V3.xx.01.15 [http://www.samsung.com/ca_fr/support/model/ML-2165W/XAA-downloads#](http://www.samsung.com/ca_fr/support/model/ML-2165W/XAA-downloads#)

I also used the xp guest to setup the wireless connection with EWS_V3.60.40.0.exe [http://www.samsung.com/ca_fr/support/model/ML-2165W/XAA-downloads#](http://www.samsung.com/ca_fr/support/model/ML-2165W/XAA-downloads#)

The ML-2165w is now working perfectly, wirelessly connected and is a swift little laser printer if I may add.

---

### Post by mr.alan.andrew on 2013-11-03
Thank you very much. I bought a printer last Christmas as a present to ME. I just got it to work, using your suggestion. After 10 months I can enjoy my present!
Alan in Vancouver BC

---

### Post by spamazure on 2013-11-05
I bought the subject printer and just installed in on my 12.04 x86_64 ubuntu.
There were no problems with installing samsung drivers for usb connected printer and make it printing via cups.

But the subject of interest for me were to setup wireless printing.
Here are the steps I done to make it work:
Wireless setup:
1) download [http://downloadcenter.samsung.com/content/DR/201110/20111019151150392/PSU_1.01.tar.gz]("http://www.samsung.com/ru/support/model/ML-2165W/XEV-downloads#") 

2) unpack, goto Linux directory, you'l find there the following list of dirs:
addressbookemailbook
phonebook
psu
wirelesssetup

wirelesssetup/bin64 contains a binary that seems to be interesting, but lacks installed libraries
Fortunately, psu/share/lib64 contains required libraries that are missing on my system, and the missing  libstdc++.o.5.0.7 can be found in psu/share/libstdc++-5-x86_64.tar.gz

So I make copy of these libraries to the /usr/lib/ then
cd /usr/lib
ln -s libsnmp.so.15.1.2 libsnmp.so.15
and viola! wirelesssetup now can be launched... but it requires a device as an argument.

3) launch sudo ./wirelesssetup /dev/usb/lp0
setup wireless network
4) access printer via [http://ip.in.your.network/](http://ip.in.your.network/)
5) login as admin / sec00000
6) configure all remaining options

As you see in the admin interface printer provides access to itself via ipp and lpr protocols, so now it's easy to use it as a network printer.

---

