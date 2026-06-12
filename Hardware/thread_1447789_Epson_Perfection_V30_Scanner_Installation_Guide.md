---
title: "Epson Perfection V30 Scanner Installation Guide"
date: 2010-04-05
forum: Hardware
---

### Post by maclenin on 2010-04-05
**UPDATED JUNE 2012**

Having (just) purchased an **Epson Perfection V30** scanner and successfully installed and scanned and printed an image / document (in Xubuntu Intrepid & Natty & Precise), I wanted to share my experience via this mini "how-to":

1. Plug the scanner into an electrical outlet via power cord.

2. Plug the scanner into a computer via usb cable.

3. Press the power button on the scanner (turning it ON).

4. Download the **libtdl3** .deb from [_here_]("https://launchpad.net/ubuntu/intrepid/i386/libltdl3/1.5.26-1ubuntu1") (NB: You may not need **libtdl3** for release [COLOR="DarkOrange"]**>**[/COLOR] **8.10**).

5. Download the **iscan "data package"** .deb [ **iscan-data_x.x.x-x_all.deb** ] for release **[COLOR="DarkOrange"]<[/COLOR]** **12.04**, [_here_]("http://www.avasys.jp/lx-bin2/linux_e/scan/DL2.do") or for release **12.04**, [_here_]("http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=17168&DSCCHK=cf127314cd4a72b9e369e7b721953185bf2a9e1a").

6. Download the **iscan "core package"** .deb [ **iscan_x.xx.x-x.ltdlx_i386.deb** ] for release **[COLOR="DarkOrange"]<[/COLOR]** **12.04**, [_here_]("http://www.avasys.jp/lx-bin2/linux_e/scan/DL2.do") or for release **12.04**, [_here_]("http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=17168&DSCCHK=cf127314cd4a72b9e369e7b721953185bf2a9e1a").

7. Download the **esci-interpreter "core package"** .deb [ **esci-interpreter-gt-fxxx_x.x.x-x_i386.deb** ] for release **[COLOR="DarkOrange"]<[/COLOR]** **12.04**, [_here_]("http://www.avasys.jp/lx-bin2/linux_e/scan/DL2.do") or for release **12.04**, [_here_]("http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=15840&DSCCHK=898b036aaff83c22e655400712324b9c26974a86").

8. Install the files in 4, 5, 6, 7 order.

9. Go to Applications / Graphics / Image Scan! for Linux - and enjoy!

NB: I had to toggle my scanner OFF and then ON again for the software to "find" my scanner (Natty & Precise). 

I hope this helps!

NB: The V30 is a great scanner!

Happy scanning!

---

### Post by kaibob on 2010-05-30
I received an Epson V30 scanner two days ago and thought I would add a few comments:

* I pretty much followed the installation procedure noted by maclenin. I'm running lucid and did not install libtdl3.deb. The scanner was recognized after a computer reboot.

* The V30 works well with the Epson Image Scan software. My only reservations are that most settings are not remembered from session to session and the program is slow to load on my somewhat aged computer. 

* The scanner also works well with the Simple Scan program included with lucid. I primarily scan text documents, so I will probably stick with Simple Scan for day-to-day use.

* Overall, I like the V30 scanner. Warm-up is about about 3 seconds, and scans are faster than on my old Epson 3490 scanner. Also, the V30 is relatively quiet compared with the 3490.

Just as a point of information, Epson is scheduled to replace the V30 with a model V33 in mid-June. Before purchasing this scanner, driver availability should be checked at:

[http://avasys.jp/eng/linux_driver/](http://avasys.jp/eng/linux_driver/)

*** EDIT 06.25.10 ***

Epson uploaded new files this morning for the V30 and V300 scanners. These files also add support for the just-released V33 and V330 scanners. 

In my case, the new files are:

> iscan-data_1.0.0-2_all.deb

iscan_2.25.0-1.ltdl7_i386.deb

esci-interpreter-gt-f720_0.0.1-2_i386.deb

The installation instructions state:

> There are two packages for installing Image Scan! for Linux: core
package and data package. To install Image Scan! for Linux, install data
package, and then install core package.

I decided to upgrade to the new versions and had to first uninstall the old iscan and esci packages with synaptic. I then installed the new versions in the following order:

> iscan-data_1.0.0-2_all.deb

iscan_2.25.0-1.ltdl7_i386.deb

esci-interpreter-gt-f720_0.0.1-2_i386.deb

After a reboot, everything worked fine.

---

### Post by Marky_boi on 2011-02-05
I just bought a V33 and it just works as per instructions..
Thanks fellow penguinistas!!
Here are the latest file versions..

iscan-data_1.6.0-0_all.deb
iscan_2.26.1-3.ltdl7_i386.deb
esci-interpreter-perfection-v330_0.0.1-1_i386.deb


Mark

---

### Post by fjgaude on 2011-02-16
> **Marky_boi said:**
> I just bought a V33 and it just works as per instructions..
Thanks fellow penguinistas!!
Here are the latest file versions..

iscan-data_1.6.0-0_all.deb
iscan_2.26.1-3.ltdl7_i386.deb
esci-interpreter-perfection-v330_0.0.1-1_i386.deb

Mark

I too just purchased a V33 and everything is working but with a few strange issues.

I need to run SimpleScan before the iScan, Image Scan works. The on/off sw works if iScan is not loaded.

Really pleased with the GUI menu and the clean scans of the V33. It's so fast compared to my last scanner. I love the LED backlighting, and that's an aspect of its quickness to come up and be ready to scan.

Now looking for a driver for my Epson R220 printer. <smile>

---

### Post by lavinog on 2011-03-15
I was looking at getting the V33 since I hear that it works in linux...however it appears that you have to install a third party driver.  Is this the case, or will the scanner work with a default Ubuntu install?

---

