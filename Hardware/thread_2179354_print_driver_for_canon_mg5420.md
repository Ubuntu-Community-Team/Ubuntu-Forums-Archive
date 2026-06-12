---
title: "print driver for canon mg5420"
date: 2013-10-07
forum: Hardware
---

### Post by Paul Barnett on 2013-10-07
Has anyone found a print  driver for a canon pixma MG5420 multifunction printer or  a workaround?

---

### Post by cooper-noah on 2013-10-08
[http://www.driverlook.com/canon-pixma-mg5420-wireless-printer-driver-linux-ubuntu-mint-mac-os-x/](http://www.driverlook.com/canon-pixma-mg5420-wireless-printer-driver-linux-ubuntu-mint-mac-os-x/)

i just googled this question myself for the second time and it looks like there's a driver now.  no clue where it came from, but it just printed something perfectly over the wLAN.  note that the install.sh file should end up configuring your printer from the console.  i thought it didn't work, so did less install.sh and saw a whole script that didn't run.  so, if it doesn't then pay attention to what required packages you need.  alternatively installing the proper .deb file with dependencies automatically downloaded may work, too.  no clue on that or the scanner bit.

cheers

---

### Post by Paul Barnett on 2013-10-08
Thanks. Can you show me the steps for installing this file? Thanks again

---

### Post by daniel_wang2 on 2014-04-21
Canon does not provide Linux drivers on their US and Canada websites, but you can find them on the Canon Asia and Europe sites.  I have a networked MG5420 printer and I've gotten it installed and working from my Ubuntu 13.10 workstation by downloading and installing the MG5400 series driver from the Canon UK site (even though I am a US customer).

Click [here]("http://www.canon.co.uk/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MG_series/PIXMA_MG5440.aspx?DLtcmuri=tcm:14-994983&page=1&type=download") to go to the download page from the Canon UK site that allows you to download the Linux/Ubuntu printer driver for the MG5420.  Note that the specific model selected is the MG5440, but the driver is for the entire MG5400 series (including the MG5420).

To install, extract the contents of the downloaded tar.gz file, open a terminal window and navigate to the folder containing "install.sh" file from the extracted contents.  Type "sudo ./install.sh" to launch the install script.  

Once the install script starts and gets to the "Register Printer" step, it will ask you to ensure your printer is connected to the LAN or to your computer via USB (turn the printer on if it's not already on).  Press Enter to continue.

The next step is the "Connection Method".  Type 1 for USB or 2 for network (mine was on the network LAN, so I chose 2).  The script may take a while while it searches for printers, but it should eventually display a list of available printers.  Select the appropriate printer and press Enter.

Press Enter to keep the default printer name (MG5400LAN).

Press Enter to set the printer as the default printer and you are done.  You can also download the Linux/Ubuntu scanner driver [here]("http://www.canon.co.uk/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MG_series/PIXMA_MG5440.aspx?DLtcmuri=tcm:14-994987&page=1&type=download"), but I haven't tried that yet. 

Hope this helps.

---

