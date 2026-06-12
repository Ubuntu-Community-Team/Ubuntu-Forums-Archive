---
title: "Which duplex laserprinter for 14.04 64-bit should I buy?"
date: 2014-05-31
forum: Hardware
---

### Post by ernstblaauw on 2014-05-31
At the moment, I got a Canon LBP7200Cdn printer. I cannot get this printer to work. Reading all forums, this has to do with the limited 64-bit support in the Canon drivers.

Therefore, I want to buy another printer that is supported. I got the following wishes:
[LIST]
[*]Laserprinter
[*]Duplex
[*]Support for 14.04 / 64-bit
[/LIST]

Color would be great, but a good b/w printer is also fine.

My question: which printer should I buy? I read HP has good support, but also Brother (which is cheaper) does a good job. I'm not sure if the Brother supports duplex under Linux. Can people over here comment on this? 

Thanks!

---

### Post by ernstblaauw on 2014-06-01
Can anybody help me choosing?
At the moment, I am thinking about the HP Laserjet Pro 200 Color MFP M276n. THis is the cheapest color laser printer with duplex support from HP. I believe HP is the only one with decent Linux drivers. Am I correct? Should this one work fine under 14.04?

---

### Post by tgalati4 on 2014-06-01
I don't have that particular printer, but I do have several mono and color HP laserjets and they all work fine under 12.10.  The CUPS drivers for HP printers have been around a while and the printing engines have not changed that much.  The quality of HP printers has not improved over the years, so don't expect high throughput with high reliability.  Read the web reviews on the printer of interest to see if the reliability is what you expect.

Install the *hplip*  package so you get all of the HP utilities:

hp-align (1)         - Printer Cartridge Alignment Utility
hp-check (1)         - Dependency/Version Check Utility
hp-clean (1)         - Printer Cartridge Cleaning Utility
hp-colorcal (1)      - Printer Cartridge Color Calibration Utility
hp-devicesettings (1) - Device Setup Utility
hp-fab (1)           - Fax Address Book
hp-faxsetup (1)      - Fax Device Setup Utility
hp-firmware (1)      - Firmware Download Utility
hp-info (1)          - Device Information Utility
hp-levels (1)        - Supply Levels Utility
hp-linefeedcal (1)   - Printer Line Feed Calibration Utility
hp-makecopies (1)    - Make Copies Utility
hp-makeuri (1)       - Device URI Creation Utility
hp-pkservice (1)     - Policy Kit Service
hp-plugin (1)        - Plugin Download and Install Utility
hp-pqdiag (1)        - Print Quality Diagnostic Utility
hp-print (1)         - Print Utility
hp-printsettings (1) - Printer Settings Utility
hp-probe (1)         - Printer Discovery Utility
hp-query (1)         - Model Query Utility
hp-scan (1)          - Scan Utility
hp-sendfax (1)       - PC Sendfax Utility
hp-setup (1)         - Printer/Fax Setup Utility
hp-systray (1)       - System Tray Status Service
hp-testpage (1)      - Testpage Print Utility
hp-timedate (1)      - Time/Date Utility
**hp-toolbox **(1)       - HP Device Manager
hp-unload (1)        - Photo Card Access Utility
hp-wificonfig (1)    - Wifi Configuration Utilit

---

### Post by ernstblaauw on 2014-06-01
> **tgalati4 said:**
> I don't have that particular printer, but I do have several mono and color HP laserjets and they all work fine under 12.10.  The CUPS drivers for HP printers have been around a while and the printing engines have not changed that much.  The quality of HP printers has not improved over the years, so don't expect high throughput with high reliability.  Read the web reviews on the printer of interest to see if the reliability is what you expect.

Install the *hplip*  package so you get all of the HP utilities:


Thanks. I'm not particular enthousiastic about HP, but I do not see other options brands delivering drivers for 64-bit. I never succeeded in getting my Canon LBP7200Cdn to work under 12.04 64-bit. 

So, if other people can point me to other brands / printers who work under 14.04, I would love to know.

Edit: I just read the duplex support is limited to 'manual' duplex: the driver points me to turn the page. So, this is no solution for me. Has anyone experiences with Brother printers?

---

### Post by gifford on 2014-06-01
Brother has good Linux support and their printer quality is good. I have always had success with 64-bit installs and operation.

---

### Post by tgalati4 on 2014-06-01
I have a couple of duplex printers and they work out-of-the-box.  You may have to tell the device installer that the printer has a duplexor installed, then you can get to a menu that allows you to select duplex printing and the orientation of the backside pages.  Only really old printers require manual duplex flipping--or a duplex printer that is not set up correctly.

---

### Post by ernstblaauw on 2014-06-02
Well, for example the HP LaserJet Pro 200 Color MFP M276n, which is a current HP model, features 'manual duplex mode': you have to turn the pages yourself.
I ordered a Brother HL-2250DN and I hope this printer will bring me more luck than the Canon LBP7200Cdn.

---

