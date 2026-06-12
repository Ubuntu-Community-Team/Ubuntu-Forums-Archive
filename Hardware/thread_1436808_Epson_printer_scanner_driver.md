---
title: "Epson printer scanner driver"
date: 2010-03-23
forum: Hardware
---

### Post by hashed on 2010-03-23
I was able to get Epson Stylus TX111 working with Ubuntu 8.04, with all updates installed. This method assumes you have CUPS installed.
It is important to use CUPS for adjusting final settings for this printer.!!

This method is useful for a  large number of Epson devices.

**Procedure:**

1. select the printer model number from
 [www.avasys.jp/lx-bin2/linux_e/spc/DL1.do](www.avasys.jp/lx-bin2/linux_e/spc/DL1.do)

2. download the following files
  >> iscan_2.24.0-4_i386.deb
  >> pips-snx110-ubuntu8.04-3.8.0-CG.tgz
  >> user-manual.txt

3. install the iscan debian package which is the scanner driver, then connect the device. this should get the scanner working. you will see a program installed in your main menu > graphics>Image scan for linux.

4. follow the steps in the user-manual to install the printer driver.
i.e
As root - Run the following
```

tar xvzf pips-snx110-ubuntu8.04-3.8.0-CG.tgz
./pips-snx110-ubuntu8.04-3.8.0-CG.install

```

select model number in the dialog box that pops up the end of the install.

5. for the final settings: 
(1) Start a web browser.
(2) Enter the URL "localhost:631" to display the CUPS setting screen.
(3) Click "Add Printer".
(4) Enter the printer setting name in "Name", and click "Continue".
    (5) If you wish to use the USB printer, set "EPSON Inkjet Printer #1 (Photo Image Print System)" in "Device", and click "Continue".
    (6) Set "EPSON" in "Make", and click "Continue".
    (7) Set the printer name in "Model", and click "Continue".
Note: for connecting this printer thru a network refer to user manual.


Many thanks for some helpful threads, hope this is of use to future epson users who are swirtching to ubuntu.

---

### Post by squiddy on 2010-06-22
thanks!

---

### Post by forent on 2011-01-11
thanks .. im using ubuntu 10.10 maverick meerkat. i have to download this file first iscan-data_1.6.0-0_all.deb before i apply iscan_2.26.1-3.ltdl7_i386.deb for the scanner..thanks a bunch...

---

