---
title: "Sahara 1200CU desktop scanner error"
date: 2007-02-06
forum: Hardware &amp; Laptops
---

### Post by Lutherian on 2007-02-06
Hi all. In the past I've tried plugging in this USB Desktop Scanner [Sahara 1200 cu] with Ubuntu 5.10 - Sane would simply repond "no device found" I then loaded Ubuntu 6.06 LTS on my "Main PC" - CD Bootup - this time Sane identified the scanner as "BearPaw 1200 cu" , yet was unable to use this device ... apologies, I should've recorded the error message - but I'm back in windoze mode currently. BTW - sane also picked up my TV capture card and actually took snapshots from on the the TV channels! (Perhaps not useful info however)

In my searches I read about command lines that could be added to one of the Sane config files. If there is any such code for the Sahara 1200 cu? Thanks in advance - this device is the last obstacle in my transition from Windows to Linux, so phew! Just before Vista hits the stores! LOL

Scanner Details:
==========
Sahara 1200cu
Desktop model
USB only (no power supply)
Identified in Windows as 1200 CU Plus WIA Scanner
Purchase about 4 years ago

---

### Post by Lutherian on 2007-03-21
OK, I got my scanner working - it was a long winding road with lots of stops and starts:
99% was answered via a how-to (lost the authors details will include later for credits)

Here's my basic advice:
Although one can find drivers for scanners from **[http://www.meier-geinitz.de/sane/gt68xx-backend/firmware/](http://www.meier-geinitz.de/sane/gt68xx-backend/firmware/)** the problem is that you may not download the correct driver the first time round, so the best option is to get the driver off the  CD that came with your scanner.

BUT!!! It's not that simple ....

The file you're looking for xxxx.usb will probably NOT be readily available on the Driver CD because it's hidden inside a Setup file. What I did was, to install the Driver on a windows machine and then search for the xxxx.usb file which I found under.

[CENTER]C:\Windows\System32\driver[/CENTER]

So how does one know which file to search for?
Ubuntu identifies the Scanner type (For Example - My Scanner was labeled as "Sahara" but Ubuntu Identified my Scanner as a "BearPaw 12000 CU" I immediately ignored "Sahara" as this is just the trade name, probably some company that bought some patent rights and re-manufactured the BearPaw under license. In any case, I got the *general* naming convention from **[http://www.meier-geinitz.de/sane/gt68xx-backend/firmware/](http://www.meier-geinitz.de/sane/gt68xx-backend/firmware/)**
and then searched for it in Windows (after I installed it). 
Use the search function in Windows 

[Start]>[Search]>[files and folders]>[all files and folders]>[all or part of the filename] [*.usb]


Once I had this file in my hands, I copied the xxxxx.usb file to my **Ubuntu Desktop **from there I followed the How-to:

============================================
Open the Terminal(Applications>Accessories>Terminal)

Code:
sudo cp ~/Desktop/xxxxx.usb /usr/share/sane/gt68xx
cd /
cd /usr/share/sane/gt68xx


NOTE if you don't have the driver then try downloading from the site as follows:

Code:
sudo wget [http://www.meier-geinitz.de/sane/gt68xx-backend/firmware/sbfw.usb](http://www.meier-geinitz.de/sane/gt68xx-backend/firmware/sbfw.usb)
Then open the gt68xx.conf file for editing:

from here, edit a config file as follows

Code:
sudo gedit /etc/sane.d/gt68xx.conf
Replace / Uncomment:

Code:
#override "mustek-scanexpress-1200-ub-plus"
With:

Code:
override "mustek-scanexpress-1200-ub-plus"

Done.

---

### Post by linux_luke on 2007-12-26
i actually have the mustek bearpaw 1200cu that used to work under gutsy
and no matter what i do wont work now

i changed a motherboard a few weeks ago (unrelated i know)
cuz it had a problem, i had gutsy installed and everything worked including the scanner
the only thing was diffrent was the kernel that changed after the new install
from 386 to general i changed that to try didnt work
i added the driver from the site and when that didnt work i took it from windows install
the error that i get is:
failed to open device gt68xx:libusb:001:021: invalid argument
when i type scanimage -L the output is
device `gt68xx:libusb:001:021' is a Mustek BearPaw 1200 CU flatbed scanner

under hardware information it's not registerd
anybody have a solution?

---

