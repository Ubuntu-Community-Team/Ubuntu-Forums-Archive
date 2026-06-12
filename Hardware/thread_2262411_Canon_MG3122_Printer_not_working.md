---
title: "Canon MG3122 Printer not working"
date: 2015-01-24
forum: Hardware
---

### Post by djailer on 2015-01-24
I have 14.10 and am trying to use an MG3122 printer.  I can no longer print or scan via wireless.  It has worked before, when before I upgraded 14.04 to 14.10.  I had to delete the printer and re-install but didn't think to copy the settings so now I have to recreate the printer. 

I am using the Canon PIXMA MG3122 - CUPS+Gutenprint v5.2.10 driver.  The device URI is ipps://doug.local:631/printers/Canon.

I recently also changed the router I am using.   NETGEAR WNDR4300.   I think the printer was working before I went to the NETGEAR.   I can get to the settings on the printer itself and the Wireless LAN is enabled and the Link Status shows Active.   In the NETGEAR Genie I can see the Printer as a connected device.    The IP is shows is the same one that shows up on the printer settings printout.  I can print a test page from the printer itself, but when I try to get a test page from either CUPS or the Printers option it stalls at 'Processing.   Waiting for job to complete.'   CUPS says 'Printing page 1, 20%'.  The CUPS error log doesn't show anything but the access log shows this:
```
localhost - - [24/Jan/2015:12:36:06 -0800] "POST / HTTP/1.1" 200 276 Create-Printer-Subscriptions successful-ok
localhost - - [24/Jan/2015:12:36:06 -0800] "POST / HTTP/1.1" 200 276 Create-Printer-Subscriptions successful-ok
localhost - - [24/Jan/2015:12:36:07 -0800] "POST / HTTP/1.1" 200 276 Create-Printer-Subscriptions successful-ok
localhost - - [24/Jan/2015:12:36:07 -0800] "POST / HTTP/1.1" 200 276 Create-Printer-Subscriptions successful-ok
localhost - - [24/Jan/2015:12:38:46 -0800] "POST /printers/Canon HTTP/1.1" 200 413 Print-Job successful-ok
localhost - - [24/Jan/2015:12:39:00 -0800] "POST /jobs HTTP/1.1" 200 143 Cancel-Job successful-ok
192.168.1.5 - - [24/Jan/2015:12:39:00 -0800] "POST /printers/Canon HTTP/1.1" 200 175 Cancel-Job successful-ok
192.168.1.5 - - [24/Jan/2015:12:39:04 -0800] "POST /printers/Canon HTTP/1.1" 200 225 Validate-Job successful-ok
192.168.1.5 - - [24/Jan/2015:12:39:04 -0800] "POST /printers/Canon HTTP/1.1" 200 181 Create-Job successful-ok
192.168.1.5 - - [24/Jan/2015:12:39:04 -0800] "POST /printers/Canon HTTP/1.1" 200 105030 Send-Document successful-ok
localhost - kenneth [24/Jan/2015:12:41:19 -0800] "GET /admin/log/error_log HTTP/1.1" 200 2313 -

```
The IP listed on my router for this printer is 192.168.1.18.   Is there a reason that doesn't match up to the log IP address?  Is there somewhere else I can look to find out why I cannot print/scan?  If I look at the Printer
properties and look at the print queue it shows  'Test Page Pending - Printer Error'.  I am not sure where to find the error log for this?

Thanks for any guidance or direction!!

Doug

---

### Post by ajgreeny on 2015-01-24
I suspect the printer was using a different IP on the old router and your computer us still trying to find it at the old IP, so it may be worth uninstalling the printer totally from the computer Printer dialogue, and then installing it again either from the Printers dialogue,  allowing the system to locate it, or the cups webadmin page at **[http://localhost:631/](http://localhost:631/)**.

---

### Post by pdc on 2015-01-26
Hi djailer; I see you "upgraded" from 14.04 to 14.10 and the problem is 14.10 runs out of support in about six months; whereas the 14.04 that you were on is a long-term support release; and it will be supported fully till 2019 

[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

_______________

one option for you over this recent issues is to install the drivers that Canon supply for your printer; Canon supply an install script; so when one runs it; if the wireless printer is "talking" to the router; that the install script will see it and configure it for you; if you would like guidance on that, please say

---

### Post by djailer on 2015-01-26
I was able to resolve this by hard wiring the printer to my box and configuring via CUPS.  It recognized it and now - miraculously - we can all access it wirelessly and print docs from any of the laptops.  Curious, but if it works..... :)

---

### Post by djailer on 2015-02-13
OK, not so fast.   Now one laptop is no longer able to print - it sees the printer, I can put the IP in and get to the printer's setup screen but when I try a test page I get a message 'Processing  - unable to locate printer'.   I presume that means the wireless signal is going to and from the printer and laptop.   One day it worked, now it doesn't.  I tried re-installing from the Printers menu and it installs but no change.  I cannot make any changes from the CUPS web interface on the laptop - I keep getting the Authorization user/password window over and over.  It works over the USB connection to my main desktop.   It still prints from the other laptop so we made sure all the settings were the same but no luck?    I made the printer IP static so the router always uses the same address and read something about putting the IP address in the printer settings instead of the name but I can't seem to get that right.   I am not sure what else needs to be in the device URI.  I was trying ipps://192.138.1.18

I can see several jobs I sent via CUPS but they all say pending and the top one tells me 'Unable to locate printer "Canon-MG3122.local"."

Any ideas??  I noticed that when I connect to CUPS on the laptop it says it is CUPS 1.7.2 and there are four stuck jobs.  When I log in using the wired printer I see no jobs and CUPS 1.7.5.  Any idea what that is telling me?   I used the same URL ---  localhost:631.  All are using 14.10 and it worked on 14.04?

---

### Post by pdc on 2015-02-13
I wonder if one was to start again.........how it would all go ............

1) connect printer to router wirelessly: instructions as per the attached thumbnails; .........taken from a 3100 series instruction manual ........and described here [http://www.canon.co.uk/Support/Consumer_Products/PIXMA_Printer_Wireless_Connection_Setup/MG3150_Printer_Wireless_Connection_Setup/index.aspx](http://www.canon.co.uk/Support/Consumer_Products/PIXMA_Printer_Wireless_Connection_Setup/MG3150_Printer_Wireless_Connection_Setup/index.aspx)

..............essence is by pushing the 2 buttons in the thumbnails..............the 3100 transmits..................you press the WPS on the router and the 2 are friends .........................

............check it is seen with ```
/usr/sbin/lpinfo -v
```

2) install the Canon drivers from here (instead of using gutenprint): [http://support-asia.canon-asia.com/contents/ASIA/EN/0100393702.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100393702.html) and you will download cnijfilter-mg3100series-3.60-1-deb.tar.gz

..............however you will need [COLOR="#0000FF"]libtiff4[/COLOR] as Ubuntu withdrew it............so get it from here [ftp://ftp.us.debian.org/debian/pool/main/t/tiff3/](ftp://ftp.us.debian.org/debian/pool/main/t/tiff3/) and get either 32bit or 64bit: 14 or 17 down the list .............

to install the Canon file that is cnijfilter-mg3100series-3.60-1-deb.tar.gz, the commands are:

cd Downloads 
tar -zxvf cnijfilter-mg3100series-3.60-1-deb.tar.gz
cd cnijfilter-mg3100series-3.60-1-deb
./install.sh 

the last command runs the install script: if step 1) went well the Canon will be spotted; drivers installed and the printer registered in lpadmin

________________

finally......................open the printer box: menu/admin/printers? ...........top left...............server settings............ensure the device is shared .................

---

### Post by djailer on 2015-02-13
Cool.  Easy to follow and the test page printed great.   I had heard of getting Asian drivers but stopped looking when it worked initially.

Thanks LOTS!!!!:guitar:

---

### Post by pdc on 2015-02-15
delighted to hear all is working well for you; thanks for the feedback: enjoy the printer!

---

