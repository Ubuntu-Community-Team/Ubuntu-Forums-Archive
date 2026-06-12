---
title: "The problem with the modem in ubuntu"
date: 2007-06-08
forum: Hardware &amp; Laptops
---

### Post by q8-77 on 2007-06-08
Good morning or good evening, I want to help the new joint Do I find here I am using "Ubuntu 7" and I want to run modem so that I could enter the Internet problem is (that has no modem (Creative blaster pci di5663), and modem-type (driver) Is here a solution to this problem 

Please help as soon as

God protect you

---

### Post by poe503 on 2007-06-09
I never had much luck getting linux to recognize pci modems.  Best to use an external modem that connects to a standard serial port.  I use an old US Robotics modem though probably most any external modem will do.

---

### Post by q8-77 on 2007-06-09
My friend the candidates me, I used this modem or used - if there was any way you help me I should be thankful. ;)

---

### Post by t4thfavor on 2007-06-09
As a general rule, anything that connects to a serial port will work under Linux. Try a US Robotics courier, or a sportster series modem. You can pick them up on ebay for just a few dollars American.

---

### Post by jjordan on 2007-06-10
This appears to be a WinModem, that is to say a modem that is basically just an analog-digital converter with all of the modem functionality being handled by the main CPU.  Drivers for this class of modem are extremely problematic under Linux.

I believe this modem uses the:
GX5USA-33051-M5-E      Creative ModemBlaster DI5630(-3), Rockwell RLVDL56DPF/SP chipset.

Take a look at this page first as you need to be sure what chipset you modem is using.:
[http://linmodems.org/](http://linmodems.org/)

This page lists a driver that may work if the chiset I found is correct:
[http://walbran.org/sean/linux/linmodem-howto-5.html#ss5.5](http://walbran.org/sean/linux/linmodem-howto-5.html#ss5.5)

This is taken from that page:

"5.5 Conexant/Rockwell HSF 
There exist drivers for kernels 2.2.14, 2.2.16, and 2.2.17 at [http://www.olitec.com/pci56kv2.html](http://www.olitec.com/pci56kv2.html) The page is in French, but the installation commands are given on the page in boldface red text (you can also use the babel fish). Essentially, the instructions are to download the appropriate package, unpack it with tar -zxvf, and run the installation script ins_all. 
This driver is, however, a bit finicky (with the most common symptom of failure being the "NO DIALTONE" response), but a number of people have been able to get it to work, usually by inserting their modem's vendor ID in the modem's .inf file, perhaps along with a change of the device major number from 254 to 253. Some helpful pages include Imran Ghory's guide, and the Linmodems.org mailing list archives, such as this message, and this message about how to get the modules to automatically load. "

Good luck getting it running.  Unfortunately modems are a bit of a dying breed.

-j

---

### Post by q8-77 on 2007-06-10
The problem lies in the modem does not have any presence in (ubuntu) If the system (winxp or win 98 or all win) be present and working in the form of either a very beautiful voice Kurt is the same type of work on a very, very nice if there was assistance in this system or find an appropriate solution to the problem I put in this section

---

