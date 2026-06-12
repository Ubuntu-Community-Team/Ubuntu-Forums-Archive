---
title: "Printing in 12.04.2, Lexmark z600 driver installation"
date: 2013-03-14
forum: Hardware
---

### Post by alvinmoneypit on 2013-03-14
I have a Lexmark 1150 printer.  With the z600 driver rigged in my old 10.10 setup it worked somewhat.  When I installed 12.04.2 yesterday, the printer install program saw it as a Lexmark 1100 series printer but would not load the available driver ("internal - external server error" was approximately the error message).  I tried [this old HowTo]("https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters#Lexmark%20Z600%20Series%20Printers").  

After running the HowTo, I saw in step 9 terminaal did not return the desired result, but manually looking for the files, they seem to be in place.  When I tried to configure the printer, it was no longer visible to the program.  So I'm wondering if my system is ruined, as alluded to in the HowTo, or is there something I can do to get this system printing with this printer.  I've already rebooted several times and have disconnected the printer, rebooted, reconnected with no change.  

Thanks for all replies.

---

### Post by alvinmoneypit on 2013-03-18
I got it working by using [this HowTo]("https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters") to locate the [Z600 driver]("https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters?action=AttachFile&do=view&target=lexmark.z600-0.4.deb") and the i386 libstdc++5 I got from Synaptic. First got libstdc++5, then downloaded the Z600 driver. Get the ppd file out of the package by simply clicking on the package and extracting the ppd with Archive Manager.
    Then I installed with the onboard printer installer- 1) select printer, click forward; 2) program searches for driver, click 'cancel' if it finds one, click "forward"; 3 "Choose Driver" screen comes up, click "Provide PPD file" navigate the browser lookup to where you extracted the PPD of Z600 and click forward. Then your printer is loaded and you can try to print. Hope this works for other seekers.

---

### Post by alvinmoneypit on 2013-04-05
It looks like someone added the [Lexmark z600-0.4.deb ]("https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters?action=AttachFile&do=get&target=lexmark.z600-0.4.deb")to Ubuntu software center.  Just get it [here]("https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters?action=AttachFile&do=get&target=lexmark.z600-0.4.deb") and it should work immediately.

---

### Post by alvinmoneypit on 2013-07-04
If you are using a 64-bit version of Ubuntu, you'll need the 32 bit libs.  To get them, type or paste the following code into a terminal (CNTRL+ALT+T):```
sudo apt-get install ia32-libs alien
```
Print a test page.

---

