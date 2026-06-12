---
title: "adding Brother MFC-495CW Printer on wired network."
date: 2013-05-04
forum: Hardware
---

### Post by archp2009 on 2013-05-04
I have been trying to follow this Youtube guide [http://www.youtube.com/watch?v=bRrN3tQzfi0](http://www.youtube.com/watch?v=bRrN3tQzfi0) to add a printer that is connected to another computer on my home network to Ubuntu 12.10 but the printer cannot be found.  It is a simple inkjet printer connected to the other printer by usb.  I have no problem accessing it via Windows.  The only thing it shows in Windows when I go to print from it is \\HOME-8FDCC38182\Brother MFC-495CW Printer. I have no problem accessing files on the other computer when I click on Network Servers from Ubuntu.   I cannot see any IP assigned to the printer on the other computer when I look into Printer properties on that computer.  Any assistance would be much appreciated.

---

### Post by abrianb on 2013-05-04
Is the printer listed as shared on the pc that it is attached to?

---

### Post by gifford on 2013-05-04
Is the computer the printer is attached to running window?
Also, the video you viewed is for a free standing network printer attached by ethernet connection. Have you installed the Brother drivers on your computer?
Here are some links on how to share a windows connected printer with Ubuntu.
[http://www.watchingthenet.com/connecting-to-shared-printers-on-windows-comput](http://www.watchingthenet.com/connecting-to-shared-printers-on-windows-comput)
[http://www.7tutorials.com/how-access-windows-shared-printer-ubuntu](http://www.7tutorials.com/how-access-windows-shared-printer-ubuntu)

---

### Post by archp2009 on 2013-05-10
Thanks for the replies.  I had been anticipating an email message.  Yes, the computer the printer is attached to is running Windows XP and is shared in Windows.  I realized the fact that the video was for a true Network printer but that was the best I could find.  I do not have a Linux driver for the Brother printer on Ubuntu.  It works via Windows XP using the driver on the other computer.  I received this reply from Brother for a driver as I noticed that the MFC-495CW did not come up as an option in Ubuntu.  
[SIZE=3][COLOR=black][FONT=&amp]Seeing that they are very new operating systems, we cannot   guarantee yet but you can always try installing the driver by clicking on the   link below.  [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-495CW](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-495CW)[/FONT][/COLOR]
[/SIZE][SIZE=2]
[SIZE=1]I have no idea which one to download or how to go about installing it on Ubuntu.[/SIZE][/SIZE]

   [COLOR=black][FONT=&amp]
I set up Samba, etc., but still do not see any printers in the Printer settings in Ubuntu, just get this:  FirewallD is not running. Network printer detection needs services mdns, ipp, ipp-client and samba-client enabled on firewall.
[/FONT][/COLOR]

---

