---
title: "Hp scanner install problem."
date: 2017-07-17
forum: Hardware
---

### Post by ac7112 on 2017-07-17
Hi folks, new user Arturo here.
I'm running Ubuntu 16.04 LTS and have just purchased an HP Laser Jet Pro MFP M227fdw.  I've got the printer running using an ethernet cable connection, but can't seem to get it to detect the scanner.
I've tried installing the hplip program and the sane find scanner.  Below is the error message I've received:
Any help would be appreciated.
Thanks,
Arturo




No devices found.


---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------


 
HP-HP-LaserJet-MFP-M227-M231
----------------------------
Type: Unknown
Device URI: dnssd://HP%20LaserJet%20MFP%20M227fdw%20(0CB92A)._ipp._tcp.local/?uuid=564e4233-4331-3136-3436-c8d3ff0cb92a
PPD: /etc/cups/ppd/HP-HP-LaserJet-MFP-M227-M231.ppd
PPD Description: HP LaserJet MFP M527 Postscript (recommended)
Printer status: printer HP-HP-LaserJet-MFP-M227-M231 is idle.  enabled since Thu 13 Jul 2017 11:38:43 PM PDT
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend for HP-Devices.


OKI-DATA-CORP-MB471
-------------------
Type: Unknown
Device URI: usb://OKI%20DATA%20CORP/MB471?serial=AK26034918&interface=1
PPD: /etc/cups/ppd/OKI-DATA-CORP-MB471.ppd
PPD Description: OKI DATA CORP MB471(PS)
Printer status: printer OKI-DATA-CORP-MB471 disabled since Tue 11 Jul 2017 11:36:33 AM PUnplugged or turned off
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend for HP-Devices.




--------------
| PERMISSION |
--------------


 
-----------
| SUMMARY |
-----------


Missing Required Dependencies
-----------------------------
error: 'libdbus-1-dev' package is missing/incompatible 
error: 'libcups2' package is missing/incompatible 
error: 'libcupsimage2-dev' package is missing/incompatible 
error: 'libusb-1.0.0-dev' package is missing/incompatible 
error: 'libsnmp-dev' package is missing/incompatible 
error: 'snmp-mibs-downloader' package is missing/incompatible 
error: 'libsane-dev' package is missing/incompatible 
error: 'libcups2-dev' package is missing/incompatible 
error: 'cups-bsd' package is missing/incompatible 
error: 'cups-client' package is missing/incompatible 
error: 'libjpeg-dev' package is missing/incompatible 
error: 'python3-dev' package is missing/incompatible 
error: 'openssl' package is missing/incompatible 
error: 'python3-pyqt4' package is missing/incompatible 
error: 'gtk2-engines-pixbuf' package is missing/incompatible 
error: 'libtool' package is missing/incompatible 
error: 'libtool-bin' package is missing/incompatible 


Missing Optional Dependencies
-----------------------------
error: 'python3-notify2' package is missing/incompatible 
error: 'python3-dbus.mainloop.qt' package is missing/incompatible 


Total Errors: 14
Total Warnings: 2

---

### Post by vocx on 2017-07-19
> **ac7112 said:**
> Hi folks, new user Arturo here.
I'm running Ubuntu 16.04 LTS and have just purchased an HP Laser Jet Pro MFP M227fdw.  I've got the printer running using an ethernet cable connection, but can't seem to get it to detect the scanner.
I've tried installing the hplip program and the sane find scanner.  Below is the error message I've received:
Any help would be appreciated.
Thanks,
Arturo



```

No devices found.


---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------


 
HP-HP-LaserJet-MFP-M227-M231
----------------------------
Type: Unknown
Device URI: dnssd://HP%20LaserJet%20MFP%20M227fdw%20(0CB92A)._ipp._tcp.local/?uuid=564e4233-4331-3136-3436-c8d3ff0cb92a
PPD: /etc/cups/ppd/HP-HP-LaserJet-MFP-M227-M231.ppd
PPD Description: HP LaserJet MFP M527 Postscript (recommended)
Printer status: printer HP-HP-LaserJet-MFP-M227-M231 is idle.  enabled since Thu 13 Jul 2017 11:38:43 PM PDT
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend for HP-Devices.


OKI-DATA-CORP-MB471
-------------------
Type: Unknown
Device URI: usb://OKI%20DATA%20CORP/MB471?serial=AK26034918&interface=1
PPD: /etc/cups/ppd/OKI-DATA-CORP-MB471.ppd
PPD Description: OKI DATA CORP MB471(PS)
Printer status: printer OKI-DATA-CORP-MB471 disabled since Tue 11 Jul 2017 11:36:33 AM PUnplugged or turned off
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend for HP-Devices.




--------------
| PERMISSION |
--------------


 
-----------
| SUMMARY |
-----------


Missing Required Dependencies
-----------------------------
...


Missing Optional Dependencies
-----------------------------
...
Total Errors: 14
Total Warnings: 2

```


When are you getting these error messages? Are you running something in the terminal?

Is this your printer? It seems to be fully supported by HPLIP.
[http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_mfp_m227-m231.html](http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_mfp_m227-m231.html)

How did you install the printer? Basically, you need to turn it on, connect the printer by USB or Ethernet, and then run "hp-setup" in the terminal for HPLIP to install your printer correctly. See here [https://ubuntuforums.org/showthread.php?t=2364149&p=13658387#post13658387](https://ubuntuforums.org/showthread.php?t=2364149&p=13658387#post13658387)

If you notice, you have some dependency errors. You should install all those packages so HPLIP works without problem.
```

sudo apt install libdbus-1-dev
sudo apt install libcups2
sudo apt install libcupsimage2-dev
sudo apt install libusb-1.0.0-dev
sudo apt install libsnmp-dev
sudo apt install snmp-mibs-downloader
sudo apt install libsane-dev
sudo apt install libcups2-dev
sudo apt install cups-bsd
sudo apt install cups-client
sudo apt install libjpeg-dev
sudo apt install python3-dev
sudo apt install openssl
sudo apt install python3-pyqt4
sudo apt install gtk2-engines-pixbuf
sudo apt install libtool
sudo apt install libtool-bin
sudo apt install python3-notify2
sudo apt install python3-dbus.mainloop.qt

```

Then run "hp-setup" again and see if it goes through.

By the way, whenever you post code or terminal output in this forum please use "```
" tags. There is an opening and a closing tag.
[PHP]
[CODE]
some code or terminal output here
    it preserves whitespace and formating
sudo apt update

```
[/PHP]

---

### Post by pdc on 2017-07-19
vocx has given you some very good pointers: 

I think this device needs a very recent version of hplip         3.16.11 and for example our version of 16.04 only has 3.16.3 so you need to install from here [http://hplipopensource.com/hplip-web/gethplip.html](http://hplipopensource.com/hplip-web/gethplip.html) and that page has install instructions too: please ask for help to translate those if you need them 

our computer is set up so that if I click SAVE, the downloaded files end up in the Downloads directory so the commands I would use; after opening a terminal ....... would be

```
cd Downloads
```

```
sh hplip-3.17.6.run
``` so you should be able to paste these commands into your terminal; to paste, right-click at the text prompt and look for the menu that appears; that should offer PASTE 

and then watch the terminal as will likely ask you questions ........ that should surely fix the dependency issues and get the scanner going too 


____________

Incidentally, you can see that hplip did not install the printer as the report you gave us says > PPD Description: **[COLOR="#0000FF"]HP LaserJet MFP M527[/COLOR]** Postscript (recommended) so that is an open-source driver from within Ubuntu's database

........ so many folks praise the ease of installing HP devices but what HP provides; hplip never seems to run ...... ubuntu is able to find a *sort of near* driver and it all sort of works out .... often

---

### Post by vocx on 2017-07-19
> **pdc said:**
> 

........ so many folks praise the ease of installing HP devices but what HP provides; hplip never seems to run ...... ubuntu is able to find a *sort of near* driver and it all sort of works out .... often
I think HP is still pretty simple to install. I think hplip is great, the caveat is, it won't run by itself. It is just a matter of running "hp-setup", and in most cases it will configure everything quickly.

In this case, it seems a newer hplip is necessary, but when that is done, it should be no problem. It's also the danger of using an old, even if stable, Ubuntu LTS: the packages in the repositories become old fast. In most cases that's no issue, but occasionally having newer versions of some packages is required.

---

### Post by JonPaul on 2017-07-20
from terminal, hp-doctor might help. It will list the missing files and give you the option to add them. You may need to run it more than once.

---

