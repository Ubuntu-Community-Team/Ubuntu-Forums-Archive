---
title: "Unable to print on Star TSP100 futurePRNT printer"
date: 2010-03-01
forum: Hardware
---

### Post by hrcariagajr on 2010-03-01
Hi all,

I got here a Star TSP100 futurePRNT USB printer and i want to print on it but i was not able to do it. I'm running on Ubuntu Netbook Remix 9.10. I already added my printer in the printer configuration(the driver is downloaded automatically) then i tried to print a test page but it fails. What should I do to solve this? 

Also, is it possible to convert my printer port into a serial port(ttyS* or ttyUSB*)? Currently my device URI appears: usb://Star/TSP143%20(STR_T-001).

Thank you very much..

---

### Post by hrcariagajr on 2010-03-02
> **hrcariagajr said:**
> Hi all,

I got here a Star TSP100 futurePRNT USB printer and i want to print on it but i was not able to do it. I'm running on Ubuntu Netbook Remix 9.10. I already added my printer in the printer configuration(the driver is downloaded automatically) then i tried to print a test page but it fails. What should I do to solve this? 

Also, is it possible to convert my printer port into a serial port(ttyS* or ttyUSB*)? Currently my device URI appears: usb://Star/TSP143%20(STR_T-001).

Thank you very much..


Hi folks,

I have successfully print now in CUPS using this driver:_ _[starcupsdrv_2.3.0-1ubuntu1_i386.deb.]("http://files.drelmo.net/starcupsdrv_2.3.0-1ubuntu1_i386.deb")  Now my question is, how can i port USB to Serial? I'm trying to do this so i can send printer commands and later on get reply from the printer. 


Thanks..

---

### Post by davbren on 2010-04-29
I have sent you a personal message if you require any further help from us at Star Micronics.

To talk to the printer users should use /dev/usblp0.

---

### Post by ben72 on 2010-09-19
> **hrcariagajr said:**
> Hi all,

Also, is it possible to convert my printer port into a serial port(ttyS* or ttyUSB*)? Currently my device URI appears: usb://Star/TSP143%20(STR_T-001).



I also would like to use my USB printer (Star TSP100 ECO)as a serial printer. Did you solve this problem? Please let me know!

Thanks

---

### Post by davbren on 2010-10-08
Hi ben72,
       You can contact Star Support at [email]support@star-emea.com[/email]. May I ask why you want to use the printer as a serial device? What is your project?

---

### Post by ben72 on 2010-10-27
> **davbren said:**
> 
       You can contact Star Support at [email]support@star-emea.com[/email]. May I ask why you want to use the printer as a serial device? What is your project?

Thanks, I've emailed them now. I want to use it with OpenbravoPOS and the built-in driver for Star printers which uses the serial port.

This way the "Open drawer"-button works.

BR,

Ben

---

