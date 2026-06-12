---
title: "Printer Margins not printing correctly"
date: 2018-01-16
forum: Hardware
---

### Post by wildbuttrueblue on 2018-01-16
Ubuntu 17.04
Libre office Version: 5.4.4.2

Printer Canon MB2320

Not sure what has happened, all has been well, the printer functioning properly until I began to 'mess with' setting up templates.

Have been printing with .25 margins around the pages all along with no issues.  

1.  Cannot delete the printer from system printers.  I delete it and it comes right back.
2.  Have rebooted PC and Printer
3.  Have attempted to change printer margins to .5 and print is still being 'cut off' the page when printed.

Not sure where to go or what all information might needed.  Please let me know.

TIA

~Regards

Kevin

---

### Post by ajgreeny on 2018-01-16
Check the default paper size shown in the cups webmin page, [http://localhost:631/](http://localhost:631/), is correct for the paper you are actually using and what is set in LO; a long time ago I had what sounds like the same problem with a Brother printer which turned out to be an incorrect paper size in one or other of those two.

---

### Post by wildbuttrueblue on 2018-01-17
Appreciate your reply ajgreeny

Default settings in [http://localhost:631/](http://localhost:631/) looked fine.  Still wondering if it has to do with the second printer which I am unable to delete ???
When I attempt to delete it thru System Admin and CUPS it responds that it is deleted but immediately returns to the list.

Perhaps install CUPS and reinstall?

---

### Post by wildbuttrueblue on 2018-01-17
Removed and reinstalled CUPS - now receiving a message from LO 5.4 that the printer cannot be started?  To try and resolve this upgraded to 17.10, still receiving the same issue.

---

### Post by pdc on 2018-01-17
I am guessing you might have the gutenprint driver; (see thumbnail)

however since 17.04, Ubuntu has had airprint support; and the MB2320 is airprint-compatible; so does it appear as a driverless option? The standard would be to have a gutenprint driver

Canon release drivers for these MB devices; you might like to try that instead; here is a link to the UK Canon site [https://www.canon.co.uk/support/consumer_products/products/fax__multifunctionals/inkjet/maxify_mb_series/maxify_mb2150.aspx?type=drivers&driverdetailid=tcm:14-1533040&os=Linux%20(64-bit)&language=](https://www.canon.co.uk/support/consumer_products/products/fax__multifunctionals/inkjet/maxify_mb_series/maxify_mb2150.aspx?type=drivers&driverdetailid=tcm:14-1533040&os=Linux%20(64-bit)&language=) and if you click to download the package, and SAVE it, it should end up in your Downloads folder; if you open a terminal and paste the commands in 

```
cd Downloads
```
```
tar -zxvf cnijfilter2-5.40-1-deb.tar.gz
```
```
cd cnijfilter2-5.40-1-deb
```

```
sudo ./install.sh
```          if you watch the terminal as it runs; it may ask you questions; you might want to delete the existing icon in the PRINTERS folder before you start; if it is not working well ....... otherwise, be able to distinguish between the gutenprint and the Canon drivers ..

__________________

---

### Post by wildbuttrueblue on 2018-01-18
Spot on pdc!  When I upgraded to 17.04 it went away and went driverless.  

Totally forgot about the upgrade to 17.04 and noticing it went driverless!  Had to hardwire the printer to the network for the driver installation to find the printer.  After that working like a charm as before!  
 Was really at a loss after not having any luck and did a fresh install to 17.10, but the problem persisted.  Your message came along at the time!  Thank you!

~Respect!
Kevin

---

### Post by ajgreeny on 2018-01-21
Great news! 

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

