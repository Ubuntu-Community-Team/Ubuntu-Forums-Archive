---
title: "Epson WF 3520 printer and ubuntu 14.04"
date: 2014-11-24
forum: Hardware
---

### Post by PrinterWontWork on 2014-11-24
Hi everyone,

I bought an Epson WF-3520 printer and I'm trying to add it on Ubuntu 14.04 64 Bit. I have installed the 64 bit debian package from the Epson website, and when I try to add the printer through system settings, the printer does appear under "Network Printers".

The problem is that when I select the printer and try to proceed, a "searching for drivers" box appears, disappears, reappears, and assuming it doesn't crash I'm then recommended a HP driver instead. My printer is not in the list of Epson printers either.

I checked Synaptic Package Manager to see if the debian package is definitely installed and is the right one, and it is. I also tried various things - using a wireless card gives me the exact same problem, as does connecting it directly with a USB. I thought of reinstalling the "printers" application through Software Center but decided against it when warning notices started popping up.

I'm very grateful for any help! :)

---

### Post by richardwaldred on 2014-12-13
I have an Epson WF-4530 printer AIO. I was able to set up printing just fine on 14.10 64 bit. I rebooted after installing the Epson ESC/P-R driver. Then I added the printer through the "System Settings..." dialog. It worked great for me  - found the network printer - printing is wonderful. Scanning throught the network is a different story. I downloaded and installed the "iscan-data_1.33.0-1_all.deb" just fine. However when I try to install the USB or the network verision od iscan, it will not install and says there is a unresolved depedency for libltdl3. Utpoic has libltdl7 installed. I am confused about this. I tried looking for libltdl3 in the stware center and could not ind it there, I will google it and see how it goes. 

Good luck with your printer issue.

---

