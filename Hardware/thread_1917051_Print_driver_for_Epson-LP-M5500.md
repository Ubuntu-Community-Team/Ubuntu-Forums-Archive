---
title: "Print driver for Epson-LP-M5500"
date: 2012-01-29
forum: Hardware
---

### Post by agnewton on 2012-01-29
I have been trying to install the driver for an EPSON LP-M5500 but have been frustrated at every turn.  I am running the 64-bit version of Ubuntu 10.04.3 LTS.  I have documented the two approaches below and am open to any suggestions on how to solve this issue.  Has anyone had success installing the EPSON drivers for an LP-M5500?  Is there a simple fix that I am perhaps overlooking?

**Approach 1)** If I specify *.ppd file that is available from the driver I downloaded from the EPSON website, I get the error message:

[I]Missing Driver

Printer 'Epson-LP-M5500' requires the 'pstolpm5500.sh' program but it is not currently installed.  Please install it before using this printer.[/I]

But, this file is available in two locations on the system:  The /usr/local/bin directory and the /opt/Epson-Driver/ directory where I previously installed the Epson driver for this printer from the Epson website. If I run the shell script the output from the pstolpm5500.sh script is:* ERROR: pstolpm5500.sh: Un-known paper size*

In addition, I have made the modification to the pstolpm5500.sh file recommended here:
[http://avasys.jp/eng/linux_driver/faq/id000749.php](http://avasys.jp/eng/linux_driver/faq/id000749.php) and re-installed the drivers.

However, the error persists.

For what it's worth, in the Epson-LP-M5500-fm3.ppd file, the pstolpm5500.sh is called by the Foomatic "Configulations"

*%*********** Foomatic Configulations ************
*%pprRIP:        foomatic-rip other
*FoomaticIDs: Epson-LP-M5500 lpm5500
*FoomaticRIPCommandLine: "pstolpm5500.sh %C"


In the Ubuntu Printing GUI, I have set the default paper size to A4 (the paper in the printer).

If I use a driver from database {EPSON LP-M5500, ESC/PageS Filter [en]}, the error message is the same as above.

**Approach 2)** If use a different (but related?) driver from the database {LP_M5000 Foomatic/eplase-jp [en] (Current)}.
The printer awakens, warms up (rotates the toner cartridges), and after submitting "Print Test Page"- reports Idle-Data file sent successfully.  But, there is no test page provided.

The Ubuntu printing GUI also properly reports the toner cartridge levels.

Thank you for taking the time to consider my issue.

---

