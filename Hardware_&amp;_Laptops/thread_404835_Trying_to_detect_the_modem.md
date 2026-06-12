---
title: "Trying to detect the modem"
date: 2007-04-08
forum: Hardware &amp; Laptops
---

### Post by Compucore on 2007-04-08
Hi Folks,

I recently recived a laptop that was going to be thrown away from a colleaue of mine, The only thing majorly wrong with it is the sound card and microphone that are not working properly on it when I am working with dapper drake. Not much of a big deal for me. Since it is being used for going places and not listening to music or video yet with it. It is a laptop from IBM and I had installed Dapper drake on previous models so they have always been good in general. What I wanted to know is this I am trying to get the internal modem to be detect by dapper drake. And I had turned on in the bios the uart chip/ serial port on it. So I know it would be detect somehow.. When I go into network and do a autodetect it would not recognize it. Now I can only assume that Lenovo and IBM are still using win modems still in their current laptops. Everything else is detected without a problem. The sound card and mic I can live without since I cannot swap those out unless I find a USB sound card and mic attachment that can hook into the USB on the left hadn side of the machine. 

Here are the specs and the link for this machine from IBM.

Intel Pentium IV-M 1.6GHZ
256 megs of ram expandable to 1 gig
20 gigs of hard drive space
10/100 cat-5 network built-in from intel
wireless 802.11b

[http://www-307.ibm.com/pc/support/site.wss/product.do?template=/product.do?template=%2Fproductpage%2Flandingpages%2FproductPageLandingPage.vm&sitestyle=lenovo&brandind=10&familyind=101256&machineind=101260&modelind=102449&partnumberind=0&subcategoryind=0&doctypeind=7&doccategoryind=0&operatingsystemind=52305&validate=true](http://www-307.ibm.com/pc/support/site.wss/product.do?template=/product.do?template=%2Fproductpage%2Flandingpages%2FproductPageLandingPage.vm&sitestyle=lenovo&brandind=10&familyind=101256&machineind=101260&modelind=102449&partnumberind=0&subcategoryind=0&doctypeind=7&doccategoryind=0&operatingsystemind=52305&validate=true)

WHen I was in the network section after doing autodetect. I went as far as going to dev/modem, dev/ttys0, dev/ttys1.dev/ttys2. dev/ttys/3 to see if it would come up. And never came up with anything. so I am at a loss here. It would be nice to include it someway or another to do something with the modem as well as to maybe fax something out from it.

Compucore
:shock:

---

### Post by fseigert on 2007-04-09
What is written in the device manager? Is it listed? 
May try this: 
[http://linmodems.technion.ac.il/](http://linmodems.technion.ac.il/)
especially ScanModem Utility.
good luck

---

### Post by Compucore on 2007-04-09
Yes it is in the device manager listing here on this laptop it is marked as Intel 82801CA/CAM AC'97 modem controller with the second line under that one Modem ALSA Control Device and above that Intel 82801CA-ich3 Modem Modem ALSA Capture DEVICE

Like I mentioned before. If it was a true internal modem where there was a chipset and a uart chip for the serial connection it would not be much of a problems since most ISA and external modems were detected that way along with the throughput that it can handle. What is frustrating about these intermnal modems. Especially the PCI they are just full of Bologna. The only PCI modems I would go with personally would be from USR Robotics becuase they have have one on a PCI format where it has the UART chip and the chipset built into it where gives you no problems for any OS that can detect it all the way through. 

COmpucore

P.S. I will igve it a go with what you had suggested. Seems like it might have been a missing driver for ubuntu that it could not see it. 

> **fseigert said:**
> What is written in the device manager? Is it listed? 
May try this: 
[http://linmodems.technion.ac.il/](http://linmodems.technion.ac.il/)
especially ScanModem Utility.
good luck

---

### Post by fseigert on 2007-04-09
Could it be to have to install sl-modem? [http://wiki.ubuntuusers.de/SmartLink](http://wiki.ubuntuusers.de/SmartLink)
Only a thought!?

---

### Post by Compucore on 2007-04-09
I am taking a look into that thank god I do understand and read a little bit of German over here the instrauctions and alll that are not too too bad in reading. I went even into the synaptic package manager to see if it could be pulled off of the multiverse section. I will let you know as seeon as it gets running it just might work that suggestion.

Compucore


> **fseigert said:**
> Could it be to have to install sl-modem? [http://wiki.ubuntuusers.de/SmartLink](http://wiki.ubuntuusers.de/SmartLink)
Only a thought!?

**NOTE:** Just to let you know fselgert it worked without a problem. I was able to pull the drivers out of the multiverse and get it to work over here. It is just a weird way of doing it but after I was able to configure it and get it online it worked right afterwards without a problem.

---

