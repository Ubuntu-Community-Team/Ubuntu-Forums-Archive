---
title: "HPLIP can't find my wireless 8610 printer"
date: 2016-01-24
forum: Hardware
---

### Post by dpjpmp on 2016-01-24
Hello everyone.

 I have a Hp Officejet printer that HPLIP can't seem to find. I can install it in cups, but the scanning side of it can't be found by the installed scanning software in Xubuntu. HPLIP can't detect any printer either installed or trying to do a fresh install of the printer. Would really like to get the scanning feature working on this. All and any help would be appreciated greatly!

Dusty

---

### Post by Bucky Ball on 2016-01-24
Bit confused. How is HPLip not detecting a printer? You install HPLip and the appropriate drivers for your printer if necessary then you go to 'Printers> Add Printer'. Click on network printer and give it awhile to find one. If it doesn't find yours, the printer's wireless is not transmitting, not visible, and there is something amiss with your printer setup before you even get to installing the drivers to it.

If it does find your printer, you select it and then move on to choosing the correct driver from the options you will be presented with.

Have you set the printer up via USB first? This is generally the easier way. You need to set an IP address on the printer if you want it to work that way as it is probably 0.0.0.0 at the moment. Have you done that? Is wireless switched on? Does HP have a printer install tool that lets you set the printer's IP, etc.?

If you set it up via a cable first to ensure it is all working then switch to wireless you may have more luck. :-k

---

### Post by dpjpmp on 2016-01-24
I am sorry, I didn't make my post more clear. HPLIP gui is not seeing the printer and the scanner software installed on the system can't detect my printer/scanner.

---

### Post by Bucky Ball on 2016-01-24
Have you got it plugged in with a USB cable??? You probably need to set it up that way first and adjust/tweak the things I mentioned in my previous post. Wireless generally doesn't 'just work' with printers 'out of the box'. You need to set the IP and switch wireless on manually.

---

### Post by ajgreeny on 2016-01-24
Which version of HPLIP do you have installed; you need at least hplip-3.14.4 for that printer and if you are running trusty the current version is just too old at 3.14.3.

Go to the website [http://hplipopensource.com/hplip-web/gethplip.html](http://hplipopensource.com/hplip-web/gethplip.html) to download the most recent version and then follow the instructions at [http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html) to install it.

---

