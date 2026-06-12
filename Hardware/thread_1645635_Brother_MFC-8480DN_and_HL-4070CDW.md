---
title: "Brother MFC-8480DN and HL-4070CDW"
date: 2010-12-14
forum: Hardware
---

### Post by JMBurton2001 on 2010-12-14
Hello,

I searched and searched for some guidance for installing these printers located on a LAN. They are both connected via Ethernet and are provided an IP address via DHCP. After much hair pulling I finally found out how easy it was to install them. The trick was found in a thread started by azhermit at [http://ubuntuforums.org/archive/index.php/t-1609071.html](http://ubuntuforums.org/archive/index.php/t-1609071.html)

In the beginning he requested step-by-step instructions and received a rather curt reply and then the explanations became so convoluted as to become confusing. Add in Brother technical support's wise words and you may as well forget about installing these printers.

I'm running Ubuntu 10.04.1 LTS on a stock Toshiba Satellite 1955-S803 laptop using wired Ethernet. (The wireless for this is another story)

As for these Brother printers, they're actually pretty easy to install if they're LAN connected and run from an IP address. If they're running from a Windows share, that's a different story.

_Simple instructions:_

Step 1 - Go to System -> Administration -> Printing

Step 2 - Click Add

Step 3 - Click the + sign to the left of Network Printer

Step 4 - Wait, wait, wait, wait... for it to be discovered. BE PATIENT, the response time for me was slow.

Step 5 - Under Network Printer, highlight the network attached printer you want. Mine showed up as "Brother MFC-8480DN (PrinterFax)" BE PATIENT.

Step 6 - This is where it all goes wrong UNLESS you do the following:

6a) Get the IP address of the printer. Review your printer manual for instructions on using the LCD screen on the printer to find its IP address. (or pull it from your DHCP server if you're using one)

6b) Type the printer's IP address in the "Host" box. In my case it pre-filled it with "PrinterFax"

6c) Click the Probe button to the right of the Host box and wait.... It may or may not change the Queue.

Step 7 - Click Forward and it will start searching for drivers. When it finds them it will open a new dialog.

Step 8 - I just hit Forward on the dialog pages and accepted the defaults... You can set them to your preferences.

Step 9 - Print a test page...  :D

_Things to check:_
1. Right click on the printer and select Properties
2. The Device URI should be "lpd://NumericIPAddress/ActualQueueName". In my case it was "lpd://192.168.1.101/BINARY_P1" without the quotation marks.
3. Click on Policies and make sure Enabled is checked.

This procedure worked without fail on both the MFC-8480DN and the HL-4070CDW

---

