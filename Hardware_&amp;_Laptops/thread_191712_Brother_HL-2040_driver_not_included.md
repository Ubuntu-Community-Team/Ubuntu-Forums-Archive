---
title: "Brother HL-2040 driver not included"
date: 2006-06-07
forum: Hardware &amp; Laptops
---

### Post by Hop-Frog on 2006-06-07
My printer was recognized, but the driver was not listed in the Printing setup program.  I have not been able to get it to print with correct margins.

Brother has kindly provided Debian files for the LPR driver, found [here](http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html#de) and a CUPS wrapper, found [here](http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html#de).  These files are apparently licensed under the GNU GPL, however, I could not locate the source code.  If having the source code available would aid in getting my printer to work, I will send a request for it, however, I am inexperienced in the matter of compiling such a thing.  Installing the available Deb files allowed me to print, however, the page margins were wrong.  Text was missing along the left and right margins and the bottom text ran off the page.

I have a copy of the PPD file on CD for this printer, specifically for Windows XP or ME.  When I tried to install this driver, I received the error "Missing PPD-Adobe-4.x header at 1:'/media/cdrom0/Driver/Pcl/Win2k_xp/ENGLISH/BH2040.PPD'."  I don't know how PPD files work, so I guessed and slapped on a header from another PPD file and deleted all of the % symbols that started of lines that also returned an error.  The driver installed with these changes, but upon testing the printer, it spewed out the entire contents of my paper tray, all blank pages.

---

### Post by bergersau on 2006-06-21
I use the HL-2060 cups foomatic driver and it works for me on my server box (Fedora core 3).

---

### Post by Mel_K on 2006-07-02
I have just purchased this printer and I have followed your link to install the driver.  I can see that it is installed via the Synaptic Package manger.  

However, when I try to add a new printer,  I cannot find the files that I need to set it up.  What am I doing wrong and how did your install work?

---

### Post by ruien on 2006-07-02
Hi.

I have a HL-2030 that works with 2060 drivers but i got rpm package from Brother. The cupswrapper and lpr driver package and build debs with alien. Then i just installed them with GDebi. This also worked fine on Breezy where i did this the first time. Make sure you have lpr driver installed before installing cupswrapper. Read Brother Install HowTo and FAQ's wich are pretty good or just read [this]("http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html")

---

### Post by Hop-Frog on 2006-07-03
Okay, I got this to work in Ubuntu 6.06 using the USB connection.  The problem was not that the printer wasn't working, the test print feature in the Ubuntu printer configuration tool simply wasn't working properly.  So once I tried opening Firefox or OpenOffice.org and printing it from there, it actually works!  I will try to explain how:

[list=1][*]System ==> Administration ==> Printing[*]Printer ==> Add Printer
[*]Wait while it reads the printer database.[*]If the Step 1 screen says "Use a detected printer: Brother HL-2040 series" you are in good shape (I think).  Just click forward.[*]On Step 2, select "Brother" as the manufacturer, "HL-2060" as the model, and "hl1250 (recommended) (Suggested)" before clicking forward.[*]On Step 3, name it HL-2040 or however you like.[*]Once that is complete, right click on the newly installed printer's icon and click properties to configure it further.  You may want to make sure that the Paper size and PageRegion are set right.  Also, I do not believe these drivers support 1200x600 DPI printing, according to the manufacturers Web site so try 300 or 600.[/list]

---

