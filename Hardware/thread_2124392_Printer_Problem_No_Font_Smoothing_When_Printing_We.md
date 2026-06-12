---
title: "Printer Problem: No Font Smoothing When Printing Web Page or PDF"
date: 2013-03-10
forum: Hardware
---

### Post by neu5eeCh on 2013-03-10
I'm using a Brother 5280DW. I just installed the [PPD driver from Brother]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html"). 

The problem, however, doesn't appear to be related to the driver but appears to be Linux related.

When I currently print out a web page or PDF file, the font's appearance is like that of a dot-matrix printer. When I print out from LibreOffice, then the fonts are smoothed and laser quality.

I thought this was "normal" (just another Linux annoyance) until... I installed a PPD driver from Brother. I initially installed the wrong one. When I printed out Web Page X, the font rendition was beautiful - as if I'd printed from Libre Office! I then installed the correct PPD and the font rendition (on the same web page) was once again terrible. I re-installed the wrong PPD file, but now the font rendition is also terrible (like it's always been)?!? 

**Question: **What the heck is going on? Has anyone else run into this and solved it?

Why did it print the web page beautifully, **once**, and then never again?!?

---

### Post by pdc on 2013-03-12
perhaps if you copy and paste

> dpkg -l | grep Brother

into a terminal, and tell us what you get...... 

I would have thought that it would be best to install the full driver

in post #5 

[http://ubuntuforums.org/showthread.php?p=12342527#post12342527](http://ubuntuforums.org/showthread.php?p=12342527#post12342527)

mambo describes how he downloaded the install script that Brother provide; and how he used it to install his needed driver

......could one suggest you delete what you have installed; use the Brother install script and it will recognise the 5280DW and install the appropriate

on this page

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-5280DW](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-5280DW)

Brother list the 5280 packages: the install script will do both the lpr and cupswrapper packages........and cope with wifi

____________________

for network connection Brother comment

> Step 5b. (for Network Connection) Configure your printer on the cups web interface
    5b-1. Open a web browser and go to "http://localhost:631/printers". 
    5b-2. Click "Modify Printer" and set following parameters.

    - "LPD/LPR Host or Printer" or "AppSocket/HP JetDirect" 	     	for Device
    - lpd://(Your printer's IP address)/binary_p1 	     	                for Device URI
    - Brother 	     	                                                                for Make/Manufacturer Selection
    - Your printer's name 	     	                                                for Model/Driver Selection

...... I think the install script will prompt  you for those things

---

### Post by kurt18947 on 2013-03-12
+1 on the installer script.  I didn't find it intuitive to download and run but it works quite well.

---

### Post by pdc on 2013-03-12
I agree the "raw" Brother product needs work ..

but can I commend mambo's detailed description

[COLOR="#B22222"]in post #5[/COLOR]

[http://ubuntuforums.org/showthread.p...7#post12342527](http://ubuntuforums.org/showthread.p...7#post12342527)

[COLOR="#B22222"]mambo describes how he downloaded the install script that Brother provide; and how he used it to install his needed driver[/COLOR]

I think he gives very detailed help

---

