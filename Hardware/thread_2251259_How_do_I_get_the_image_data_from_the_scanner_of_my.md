---
title: "How do I get the image data from the scanner of my Epson multifunction printer?"
date: 2014-11-03
forum: Hardware
---

### Post by hfinger on 2014-11-03
Ubuntu 14.04 LTS Trusty Tahr
Epson Stylus TX550W All-in-One

I have an Epson multifunction on a home wifi network.

  
I have various scanner programs, several of which cause the scanner  to scan the document, but only Xsane saves the scanned image to a file.

  
I have 

  
[LIST]
[*]Image Scan! for Linux (Epson), just displays the error "Could not    send command to scanner. Check your scanner settings."
[*]sane-pygtk, scanner appears in drop-down list ("PID 0856") and scans but no image,    "Can't scan, Operation cancelled, Check scanner settings"
[*]Scan Utility 0.6.2 (Gnome Scan), recognises scanner ("Epson PID    0856") and scans, but no image file saved; and
[*]Xsane (0.998), recognises scanner ("PID 0856:192.168.0.3"), scans    preview, scans and saves image file.
[/LIST]
  
Anyone have any suggestions for getting the simpler programs working?  And where would I set the "scanner settings"?

  
Regards, 
Hedley

---

### Post by gifford on 2014-11-03
I am not familiar with the programs you listed except for Xsane. Have you tried simple scan? Does it work for you?
As for Image-Scan!, the site indicates there are separate drivers, have you installed them?

---

### Post by Mike_Walsh on 2014-11-03
Hello, Hedley.

I myself have an Epson all-in-one; a Stylus SX218.

I've only been using Linux for 6 months or so, but haven't had much trouble adjusting, due to the fact, I guess, that I've been messing about with these things for well over 30 some-odd years now.

Research in the early days suggests that ALL Epson scanners, whether separate units, OR all-in-ones, use basically the same driver & data package. If you visit the Epson download site,[ here]("http://download.ebz.epson.net/dsc/search/01/search/searchModule"), enter your model (DON'T put Epson at the beginning!).....in your case, you will need to enter "Stylus TX550W" and "Linux", and hit 'Search'.

On the next page, you will find two printer packages, and two scanner packages. You will need to click 'Download' for the 'core scanner & data' package. The next page gives you a long list of supported models (yours & mine among them). Scroll down to the bottom, and click on 'Accept'.

Now; you need TWO packages. I'm assuming, in fact, that IF you already have Image Scan! for Linux, that you've followed these steps, so don't really need me to tell you the rest. However, I WILL stress that you need the data package as well as the scanner package, and, (THIS is VERY important!), you MUST install the data package BEFORE the scanner package.....otherwise it just 'throws a wobbly' and will refuse to function. Many people don't appear to know about the 'data' package at ALL, in fact. 

You don't say whether you have a 32-bit or 64-bit system. If you have a 32-bit OS, you need the '...ltdl7_i386.deb' package; if a 64-bit, the '...ltdl7_amd64.deb' package. The 'data' package will be the 'iscan_data_1.31.0-31_all deb' one. Don't forget; 'data' BEFORE 'scanner'...!

You should find that they will install through the Software Centre, by double-clicking on the files in 'Downloads'.

I have found, through experimentation, that when you get the error message that you mention, the solution is quite simple. Cancel the error message (this closes Image Scan!); turn the printer off, wait a few seconds, then turn it back on, and launch Image Scan again. Fingers crossed, you SHOULD find it will now start up, and you can use it. This simply appears to be either a 'glitch' in the software, or else the way it's intended to work. Once it's 'up-and-running', the interface is self-explanatory.

Run the pre-scan. Select 'Scan' when this has done, and on the 'save' options, it's easiest to accept the default destination (usually /home), and just set the filename you want to save it as (making sure to save it as a .jpg file). You can experiment with the settings, but I find that the default ones (usually a dpi setting of about 150-200) work fine.

I hope this is of some use to you. Let us know how you get on, please. Hope you're enjoying warmer weather in Oz than we are up here....winter's on it's way!

Regards,

Mike.

---

