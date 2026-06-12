---
title: "HP LaserJet Pro CM1415fnw"
date: 2010-12-05
forum: Hardware
---

### Post by Ad1217 on 2010-12-05
For anyone who reads this thread:
It seems to work fine with HPLIP now.

I just got a HP LaserJet Pro CM1415fnw, and I cannot seem to install it. CUPS sees it but cannot find a driver, HPLIP cannot see it, HP has no help on their website, and when I called them up, they told me that linux was not supported (for phone tech support (the printer IS supposed to work with Ubuntu 10.04, or so their website says)), and that I should look at the support section on their website. Does anybody know how to get this working?

---

### Post by Ad1217 on 2010-12-05
I have gotten simple printing working using the HP Color LaserJet cp1514n driver, but now I am wondering about scanning.

---

### Post by tom-ubuntu on 2010-12-14
Thinking about buying this printer as well as it seems to have everything I require reading the specs.

Printing seems fine, as Ad1217 mentioned.
Did you guys get scanning to work?
Would you guys still recommend it after a week?

Many thanks

---

### Post by ischliky on 2010-12-24
I got this printer to print fine with the information in this thread.  I was wondering if anyone had any luck getting either the scanner or the wireless printing to work under linux.  Currently mine only works with USB connection however i would like to use it as intended as a network printer.

Also, if it is easier to run a cat5 to the printer and still use wireless on the laptops that would be adequate.

If anyone has solved these issues or can point me in the right direction it would be greatly appreciated.

---

### Post by hexa on 2011-01-06
I can confirm that I got wireless printing working on a 801.11b/g WPA2 network.. on ubuntu 10.04

Using the driver cp1514n like suggested above.. 

hp-setup does not see the printer though and I can't get scanning working..

Will have to wait for hplip

---

### Post by ddpublic on 2011-01-06
Same here.  Wireless and wired printing work smoothly.  Waiting for Linux driver for scanning.

Many thanks to Ad1217.

---

### Post by karlbrooks on 2011-01-07
The CM2320 driver seems to work well.  This is the newer model for the printer.  I am still trying to get the scanner part to work.

---

### Post by bcn17 on 2011-01-11
I just installed this printer via a wired ethernet cable yesterday. I can ping the "cm1415nfw MFP" just fine. I can also print via the network using the HP "Color LaserJet cm1312 MFP" drivers. I have used the Administration --> Printing application in Ubuntu. If I run hp-setup I cannot find the printer on the network. 

I cannot scan via the network (like everyone else above) unfortunatley. I can scan to a USB drive, then transfer it. But that is a pain and not optimal of course. 

It is a nice printer for all other purposes though. I went with HP because I have had good linux compaitbility in the past. Hopefully the next hplip update will support network scanning for this printer. I have a feeling it will eventually.

UPDATE: I also just tried installing the latest drivers - "hplip-3.10.9.run" The hp-setup did not find the networked printer as before.

---

### Post by mollien on 2011-01-29
I know that this thread is kind-a dead, but for those that find this, I just installed the hplip drivers version 3.11.1 from the HP Opensource website: [http://hplipopensource.com/hplip-web/downloads.html]("http://hplipopensource.com/hplip-web/downloads.html").

Download the file, follow the instructions. Everything works over network, including faxing and scanning. The process is completely painless.

These drivers will be included in Ubuntu 11.04, so soon we will not even have to do this anymore.. :-)

[Mollien]("http://www.mollien.net")

---

### Post by Ad1217 on 2011-01-29
I still watch this thread... Anyway, I think this printer is a new addition to hplip.

---

### Post by Ad1217 on 2011-01-29
though it cannot find the printer over the network

---

### Post by Ad1217 on 2011-01-31
wierd... after trying about 5 times with reboots in between, HPLIP worked!!! :)

EDIT: that includes scanning, by the way.

---

### Post by ddpublic on 2011-01-31
How did you make scanning work, please?

---

### Post by Ad1217 on 2011-01-31
you must use the HPLIP driver from here: [http://hplipopensource.com/hplip-web/install_wizard/index.html](http://hplipopensource.com/hplip-web/install_wizard/index.html)

fill out the form, then you can download.

after downloading, open a terminal.
type 
```
cd /path/to/file/
chmod +x file
./file
```
then follow the directions

---

### Post by miluethi on 2011-06-08
This worked for me with HPLIP 3.5.11:

>Hi,
> Please try these steps;
>1. Run the command 'hp-setup'
>2. Select 2nd option. (Network/Ethernet/Wireless network (direct >connection or JetDirect) on the 'Device Discovery' window.
>3. Click on 'Show Advanced Options' on the same window.
>4. Check 'Manual Discovery' check box and enter the ip address of >your printer.
>5. Select the ppd file and finish the device setup.
>
>Thanks and Regards
>Ani Balakrishnan

==> [https://answers.launchpad.net/hplip/+question/147465]("https://answers.launchpad.net/hplip/+question/147465")

Michael

---

### Post by Ad1217 on 2011-07-05
hmmmm.... wierd... On one computer it works using system-config-printer, but on the other one it doesn't work at all...

---

### Post by carpy on 2011-08-12
Thank you all.  I found this thread while searching for my next printer, and checking to see if I should buy this one for use with Linux.

Very helpful.
Matt

---

