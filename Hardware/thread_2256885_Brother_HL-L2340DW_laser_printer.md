---
title: "Brother HL-L2340DW laser printer"
date: 2014-12-15
forum: Hardware
---

### Post by Tom_Carr on 2014-12-15
I got a Brother HL-L2340DW Laser printer.   This is the number one best seller at Amazon, but it's driver is not in the driver list when I tried to install it.  What should I do?

---

### Post by plucky on 2014-12-15
> I got a Brother HL-L2340DW Laser printer. This is the number one best seller at Amazon, but it's driver is not in the driver list when I tried to install it. What should I do? 


Go [Here](http://support.brother.com/g/b/downloadlist.aspx?c=gb&lang=en&prod=hll2340dw_us_eu_as&os=128) and download and install both the Cups and Lpr Drivers and install with the Software Centre.

Good Luck

---

### Post by Tom_Carr on 2014-12-15
Thanks for the info.  Do I download the deb or the rpm?  What folder do I download it to?

---

### Post by MrSteve on 2014-12-15
download the deb files to the download folder 
go to the download folder and right click each deb file and on that menu click install with the software centre ...

---

### Post by Bucky Ball on 2014-12-15
> **MrSteve said:**
> download the deb files to the download folder 
go to the download folder and right click each deb file and on that menu click install with the software centre ...

^^^
This. After that, do the regular 'Add Printer' and you should now see the driver there for your model. ;)

---

### Post by Tom_Carr on 2014-12-17
I downloaded and installed the files as instructed.
I opened printing/localhost and clicked the add tab
It tells me to select device and gives me 3 options - 
LPT #1, 
Enter URI  
Network Printer

I select LPT #1 
I select the "Select printer from database" option, and open the list of brother drivers
The HL-L2340DW is not in the list.

What now?

And again, thanks for your help.  I feel like a slow learner and I really appreciate your efforts to help me.

---

### Post by plucky on 2014-12-17
Open a terminal and post outut for ```
dpkg -l | grep -i brother
``` will let us know if the drivers are installed.

---

### Post by Tom_Carr on 2014-12-17
tom@tom-OptiPlex-755:~$ dpkg -l | grep -i brother
ii  brgenml1cupswrapper                           3.1.0-1                                             Brother BrGenML1 CUPS wrapper driver
ii  brgenml1lpr                                   3.1.0-1                                             Brother BrGenML1 LPR driver
ii  printer-driver-ptouch                         1.3-3ubuntu0.1                                      printer driver Brother P-touch label printers
tom@tom-OptiPlex-755:~$

---

### Post by plucky on 2014-12-17
Looks like the drivers are installed.

How is the printer connected?

Try connecting by USB and power it on.

Does the "Add Printer" find it?

Usually it should find the printer on the USB connection.

Don't use LPT#1 as that is for parallel printers I believe.

Good Luck

---

### Post by Bucky Ball on 2014-12-17
Yes, as plucky suggests, connect and setup via USB to start. I'm presuming this is a wireless printer as it has the DW at the end of the name. (I have the HL-2270DW.) 

Once the printer is setup with a static IP, then you can add printer again and choose 'Network Printer' and it should show up and so should the driver. You'll end up with an entry for the printer connected via USB and the printer connected wirelessly. Don't delete the USB entry as you might want to use that later.

You can also set up printer via cups in Firefox. In the Firefox address bar type 'localhost:631'. That should bring up the cups printer window. That's how I normally go about it. 

Good luck. ;)

---

### Post by Tom_Carr on 2014-12-18
Thanks.  I will try that tomorrow and tell you what happens.

---

### Post by Tom_Carr on 2014-12-18
I tried everything you guys suggested and I still can't get it to work. I don't know if the problem is the printer, the drivers, or me.  

I can return the printer to Amazon and get my money back, which is what I am doing.  I got my old printer fixed and it is all I need for now.  When it breaks down I will ask in this forum for suggestions about an easy to add printer.

Thanks for all your help.

---

