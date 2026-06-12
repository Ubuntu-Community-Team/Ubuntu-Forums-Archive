---
title: "Canon pixma MX922 scanner drivers"
date: 2017-06-03
forum: Hardware
---

### Post by uwe-bungto on 2017-06-03
Ubuntu Studio 16.04.2
I just installed  Canon Pixma MX922 All-in-one. The printer part works using CUPS driver and the TurboPrint drivers, quality is not bad. The issue is with the scanner part. Xsane stops with a warning >  to open device 'pixma:MX922_192.168.0.104':Invalid arugument.
Where can the proper drivers be found?

Thanks

Paul

---

### Post by uwe-bungto on 2017-07-06
Hell o anyone out there??

---

### Post by pdc on 2017-07-07
sorry to hear of your problems; 

open-source scanning is driven by SANE; and their website says support for your 920 series Canon is good; that is hardly any comfort to you; the command of ```
lsusb
``` in a terminal should say ```
 04a9:176b Canon
```

what do the commands 

```
sane-find-scanner
``` and ```
scanimage -L
``` give please: if you can copy and paste the results back here

_______

I suggested to a recent post that they join the mailing-list for SANE; to seek help there; they were recommended to install the latest version of sane; one can get it from here [https://launchpad.net/~rolfbensch/+archive/ubuntu/sane-git](https://launchpad.net/~rolfbensch/+archive/ubuntu/sane-git) and the commands there are

```
sudo add-apt-repository ppa:rolfbensch/sane-git
```

```
sudo apt-get update
``` and then the proposed update should show up in your software notification icon; 

___________

your MX920 series gets mention in /lib/udev/rules.d/60-libsane.rules as ```
# Canon PIXMA MX920 Series
ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="176b", ENV{libsane_matched}="yes"
```

which is as it should be

---

### Post by uwe-bungto on 2017-07-07
Canon advertises this unit as wireless printer and scanner,  that is why it was bought to share with a number of computers. 
guess I forgot to mention that in my first mail.

---

### Post by uwe-bungto on 2017-07-07
Got it working sort of.

the 
> sudo add-apt-repository ppa:rolfbensch/sane-git
etc. did the trick.
Now to find out how to get the proper colour balance white paper is scanned and printed as grey.
 Thanks

Paul

---

### Post by pdc on 2017-07-07
glad to hear it is working Paul; and good to hear updating works; thanks for details of wireless connection; for anyone else following, Canon offer this how-to for setting up a wireless connection [http://www.canon.co.uk/support/consumer_products/pixma_printer_wireless_connection_setup/pixma_mx924_printer_wireless_connection_setup/](http://www.canon.co.uk/support/consumer_products/pixma_printer_wireless_connection_setup/pixma_mx924_printer_wireless_connection_setup/) 

I think I could also comment that scanning on Canon MF devices is easier than others: eg Epson and Brother; 

I wonder if you have xsane installed; > how to get the proper colour balance as a front-end to drive the scanner: install with ```
sudo apt install xsane
``` and you can tweak its settings to your heart's content

---

### Post by uwe-bungto on 2017-07-07
> **pdc said:**
> glad to hear it is working Paul; and good to hear updating works; thanks for details of wireless connection; for anyone else following, Canon offer this how-to for setting up a wireless connection [http://www.canon.co.uk/support/consumer_products/pixma_printer_wireless_connection_setup/pixma_mx924_printer_wireless_connection_setup/](http://www.canon.co.uk/support/consumer_products/pixma_printer_wireless_connection_setup/pixma_mx924_printer_wireless_connection_setup/) 

I think I could also comment that scanning on Canon MF devices is easier than others: eg Epson and Brother; 

I wonder if you have xsane installed; as a front-end to drive the scanner: install with ```
sudo apt install xsane
``` and you can tweak its settings to your heart's content

I have xsane there must be an ICC  that will get  a white background when a pice of white paper is scanned.

---

### Post by pdc on 2017-07-07
anything here of help? [http://www.xsane.org/doc/sane-xsane-doc.html](http://www.xsane.org/doc/sane-xsane-doc.html)

---

### Post by uwe-bungto on 2017-07-09
> **pdc said:**
> anything here of help? [http://www.xsane.org/doc/sane-xsane-doc.html](http://www.xsane.org/doc/sane-xsane-doc.html)

I think I have a solution. I had a couple ICC from Staples for their their gloss and super matte. I scanned aRGB colour wheel and the scanner picture was close to the original..
I mark this thread as solved.

Thanks everyone

---

