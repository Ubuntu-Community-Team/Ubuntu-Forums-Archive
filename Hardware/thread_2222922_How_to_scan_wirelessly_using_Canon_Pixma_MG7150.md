---
title: "How to scan wirelessly using Canon Pixma MG7150"
date: 2014-05-08
forum: Hardware
---

### Post by ubifree on 2014-05-08
I have a Canon Pixma MG7150 and am able to print to it over the wireless network from both ubuntu 12.04 LTS and 14.04 LTS using the Canon driver downloaded from Canon [here]("http://www.canon.co.uk/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MG_series/PIXMA_MG7150.aspx?type=download&page=1").  But now I want to be able to **scan** documents with it wirelessly. Does anyone know how to set this up for either ubuntu version please?  So far I've downloaded and installed the scanner driver from the previous link. But the 'Simple Scan' app just says "No scanners detected".  Does anyone know how to get Simple Scan to see the scanner over wifi?

---

### Post by pdc on 2014-05-08
Well done to get the Canon driver installed and all configured......looks like a very good printer .........what did you do to connect the printer to the router?

If your MG7100series machine was plugged in via usb cable, Simple Scan would not see it either ..............

If you have downloaded this [http://www.canon.co.uk/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MG_series/PIXMA_MG7150.aspx?DLtcmuri=tcm:14-1087939&page=1&type=download](http://www.canon.co.uk/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MG_series/PIXMA_MG7150.aspx?DLtcmuri=tcm:14-1087939&page=1&type=download)

(the debian package of [COLOR="#0000FF"]ScanGearMP[/COLOR] from Canon)

........the intent is to run [COLOR="#0000FF"]ScanGearMP[/COLOR]   as the scanning programme     ..........so if you type or paste into a terminal > [COLOR="#FF0000"]scangearmp[/COLOR] ............................it should open a dialogue page and you can run ScanGearMP .........

If it all goes well, you can create a launcher on  your desktop to automate the launching...........let us know if you want links on that ...............
_____________________________

I understand Simple Scan is a frontend for the open source scanning programme called sane [http://www.sane-project.org/](http://www.sane-project.org/) 

The hard-working volunteers of sane have provide open-source backends for many Canon devices; including many of the newer MG devices 

If you scroll down here [http://www.sane-project.org/sane-mfgs.html#Z-CANON](http://www.sane-project.org/sane-mfgs.html#Z-CANON) to MG7100 series, you can see they want testers..................... so you can contact them if you would like to help ..........they would be delighted to have your input ...

---

### Post by ubifree on 2014-05-08
You're a star - thank you very much!  Yes, scangearmp worked beautifully for scanning a document wirelessly (tested from my 12.04 system).  I didn't realise that was the intent - oops!  Good idea about contacting sane to do some testing...  I should be able to create a launcher icon; I've done it before at some point.

---

### Post by pdc on 2014-05-08
great: enjoy        ..........and the initial setting up of printer talking to router..............that went well?

---

### Post by ubifree on 2014-05-08
Yes, I don't recall any problems. I just followed the instructions on the printer's screen. You can connect using WPS or, as I did, specify your router's SSID and WPA2 password, etc.

---

