---
title: "How To Install Brother HL-6050 Laser Printer in 6.10 Edgy"
date: 2007-02-19
forum: Hardware &amp; Laptops
---

### Post by haz2a on 2007-02-19
This was the procedure I used to install a network printer (off a print server) in Ubuntu 6.10 (Edgy). A USB printer is the default and should be a little easier.

Download the LPR and CUPS drivers:-
hl6050lpr-1.1.2-1.i386.deb (or any later version) from:-
[http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html). 
and: cupswrapperHL6050-1.0.2-1-i386.deb (or any later version) from:-
[http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html) 

NB: When they talk about installing LPD/LPR[ng) first, they mean install the Brother Lpr driver before installing the Brother CUPS driver.

1. Synaptic > Install csh (doesn't work properly without!)
2. [FONT="Courier New"]sudo ln -s /etc/init.d/cupsys /etc/init.d/lpd[/FONT]  
This is a temporary link necessary for installation.
3. [FONT="Courier New"]sudo mkdir /var/spool/lpd[/FONT]  
4. [FONT="Courier New"]sudo mkdir /var/spool/lpd/HL6050[/FONT]  
5. cd to dir containing drivers.
6. [FONT="Courier New"]sudo dpkg -i --force-all ./hl6050lpr*[/FONT]  
According to Brother installation notes, any messages aboutLPD/LPRng can be ignored, eg: "unable to copy PPD file".

7. Install the CUPS Wrapper
[FONT="Courier New"]sudo dpkg -i --force-all ./cupswrapper* [/FONT]

IF get err msg: "lpadmin: Unable to copy PPD file" then 
Check that the PPD is present: /usr/share/cups/model/brhl6050_cups.ppd.
Then do:-
[FONT="Courier New"]sudo lpadmin -p 1-Whse-B6050 -E -v usb:/dev/usb/lp0 -P /usr/share/cups/model/brhl6050_cups.ppd[/FONT]
(usb:/dev/usb/lp0 is the default port used during installation. When the FAQ says 'run the command usb:/dev/usb/lp0' it really means 'use this port in the lpadmin cmd')

8. [FONT="Courier New"]rm /etc/init.d/lpd[/FONT]  (remove temp link)
9. This should now have created the printer eg: 'HL-6050-for-CUPS' as a local printer, usually with the default USB port assigned. 
It should now be possible to change the port (and name if required) of this printer, either via the Ub > Sys > Admin > Printing print mgr, or via CUPS web interface. If the updated printer doesn't work, it should be possible to create a new printer, just pointing to the PPD file location (/usr/share/cups/model/brhl6050_cups.ppd) if the model is not listed (it wasn't for me).

If problems, check the Brother FAQs eg: [http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html](http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html) -  there is a lot of useful info there.

As a last resort, the HL-6050 seemed to work quite well using Ubuntu's supplied driver for the HL-7050 - but it might damage your printer - I really don't know!

---

### Post by Turmoyl on 2007-02-19
Just use the HP LJ4 driver that's built in with CUPS.

---

