---
title: "HP Officejet 5510 works well under Hardy Edubuntu"
date: 2008-07-08
forum: Hardware
---

### Post by einfeldt on 2008-07-08
Hi, 

I wanted to let this forum know of a really good result that I had with an HP Officejet 5510 all-in-one.  It just works.  And HP or Canonical has provided a tool specifically for HP, so we should all support HP, as they apparently have been very good to GNU-Linux.  

I am using Hardy Edubuntu on an AMD 4200 with 4 GB of RAM in a Lian Li aluminum case.  I just plugged the USB cable from the 5510 into the USB port on the front of the machine, plugged in the scanner / printer / copier / fax machine and turned on the power by pressing the power button which is conveniently located on the top of the machine on the operator panel on the left hand side of the machine.  

I then went to System > Administration > Printing to configure the printer.  You can just follow the default settings, except when it comes to choosing the "device", please be sure to notice that Hardy will have found your 5510, Please be sure to arrow down once, because by default you will notice that it will be set to print to a PDF.  I chose not to do that, and chose the specific 5500 series printer located there. Please note that the actual 5510 did not show up in the list of supported printers, but that is okay.  You will be given a choice of vendors.  Hardy will automatically find that you are using an HP device.  Click on HP, then scroll down to the 5500 series.  Follow the defaults through to the end, and you will be find.  I think you have to click apply at the end, as I recall.

Now place your document on the glass for scanning.  I recommend trying just one page at first, because that is how it worked for me.  Your mileage may vary, but it worked for me, so I am just telling you what I did. 

Now that you have configured your printer, you can just go to System > Preferences and you will see the HP logo in the menu beside a menu option called HPLIP Toolbox.  Just click on that item, and you will get the SANE scanner interface that pops up.  

In the SANE user interface, please be sure to choose whether you want color or gray scale.  Also, please be sure to choose your resolution.  A scan of 75 would be fairly low, and a scan of 250 would be fairly high.  The latter scan will produce a file around 1.3 MB or so.  Then be sure to click on File > Save and be sure to choose the proper extension.  Choosing .jpeg will work for most of your needs.

HP has been good to Linux, and so let's be good to HP and go out an buy those HP products!

---

### Post by linkx on 2008-09-30
Me too! I just plugged in the USB, turned it on, and POOF! I got a notification that the 5510 was ready to use! Went to Applications > Graphics > xSane and scanning worked fine!

---

### Post by Soupcan on 2008-09-30
Almost every HP printer I've used works by simply plugging in the USB. I've never had to power cycle anything. 

HP is great.

---

