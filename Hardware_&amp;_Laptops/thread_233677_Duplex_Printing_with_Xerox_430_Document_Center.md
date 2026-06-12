---
title: "Duplex Printing with Xerox 430 Document Center"
date: 2006-08-10
forum: Hardware &amp; Laptops
---

### Post by mowestusa on 2006-08-10
We have a brand new Xerox Document Center 430ST with Network Printing. I was shocked that without a problem I got it set up in Ubuntu using the ljet4 driver. It also had the suggested driver called lj4dith. I don't know the differences between those drivers.

However, my question is I would like to be able to do duplex printing or double sided printing. Although the option is there in the print preferences it is grayed out. Anyone know if there is a way to get this working?

Do I need to install another driver?

Thanks for your help.

Steve
mowestusa

---

### Post by mowestusa on 2006-08-25
Is duplex printing a function within the printer driver?

Could I use another printer driver with the Xerox Document Center 430ST that would give me that functionality and perhaps even let me pick one of the 4 paper trays it uses?

Steve
mowestusa

---

### Post by tog on 2007-09-06
The answer is most likely. We have a 255ST and for a long time, I could not use all the features. But, I now have it successfully running. Here is what I did.

1. Down the PrinterPackageXpxx from Xerox's site. I did a search for Linux and 255 Document Center for mine. Untar the package, and within it, there is a directory called ppd.
2. Open up Printers from System, Administration. Add printer.
3. When it comes to choosing the make, choose Xerox, and then choose the option that says, "Have a driver disk." Point it to the ppd file for your printer.
4. You should now see all the options available for your printer.

If you have trouble downloading the ppd, let me know. I still have the whole folder that I downloaded.

> **mowestusa said:**
> Is duplex printing a function within the printer driver?

Could I use another printer driver with the Xerox Document Center 430ST that would give me that functionality and perhaps even let me pick one of the 4 paper trays it uses?

Steve
mowestusa

---

### Post by gis-morgan on 2008-04-02
Hi there. I know this thread is old, but I just got my Document Center 430 ST working with almost all options in Hardy (8.04 Beta) and thought I'd share.


1.)Get the PPD file from Xerox's website. At the driver portion of the site, it will ask you what operating system you're using - say WINDOWS 98. Then download the "generic PPD" file. 

2.) Open that file as root with a text editor and DELETE the line that says:
```
*cupsFilter: "application/vnd.cups-postscript 0 XeroxWCPFilter"
```

3.) In a web browser, type:
```
http://localhost:631/
```
in the address bar.

4.) Click "Add Printer"

5.) Name it something. This doesn't matter as far as the machine cares, just don't use spaces.

6.) On the "Device for <whatever you called it in the last step>" page, select LPD/LPR printer or host.

7.) On the "Device URI" page, enter the ip address of the printer like this:
ldp://192.168.1.1:lp
Of course, use your printer's ip. Don't forget the ldp:// or the :lp

8.) On the "Make/Manufacturer" page, upload that modified PPD file and click "Add Printer"

9.) Print a test page, and enjoy your new duplex-ing and tray selection options.

---

