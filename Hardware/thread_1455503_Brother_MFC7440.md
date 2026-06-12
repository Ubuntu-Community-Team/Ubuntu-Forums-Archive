---
title: "Brother MFC7440"
date: 2010-04-16
forum: Hardware
---

### Post by jimw on 2010-04-16
I got a Brother MFC7440 the other day.  At one point, I had it printing from the computer very nicely.  I couldn't seem to get it to deliver a scan to  the computer, though, so I went back to the beginning, uninstalled all the drivers, and started over again.  The result is that it doesn't print any longer.

I've managed to get to the state where the computer sees the printer; when I try to print a test page, though, I get the following:

"There was an error during the CUPS operation: 'client-error-document-format-not-supported'."

Can anyone tell me what this means, and more importantly, how to fix it?

Thanks

---

### Post by plucky on 2010-04-16
> **jimw said:**
> I got a Brother MFC7440 the other day.  At one point, I had it printing from the computer very nicely.  I couldn't seem to get it to deliver a scan to  the computer, though, so I went back to the beginning, uninstalled all the drivers, and started over again.  The result is that it doesn't print any longer.

I've managed to get to the state where the computer sees the printer; when I try to print a test page, though, I get the following:

"There was an error during the CUPS operation: 'client-error-document-format-not-supported'."

Can anyone tell me what this means, and more importantly, how to fix it?

Thanks


Open Firefox and in the address bar put ```
http://localhost:631/
``` will open the CUPS interface.

Then check the paper size is correct for the printer.

> I couldn't seem to get it to deliver a scan to  the computer

Did you install the scanner drivers?

Go [Here](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html) to download the driver.


Good Luck

---

### Post by jimw on 2010-04-16
> **plucky said:**
> Open Firefox and in the address bar put ```
http://localhost:631/
``` will open the CUPS interface.

Then check the paper size is correct for the printer.



Did you install the scanner drivers?

Go [Here](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html) to download the driver.


Good Luck


//localhost:631/[/ ends up with a blank screen.

I should have made sure in my original post to note that I'd followed the directions on the Brother solutions page, including the loading of drivers for the scanner.

JimW

---

### Post by jimw on 2010-04-18
In attempting to install the lpr driver and the cups driver, I get the following messages:

dpkg: warning: files list file for package `brother-lpr-drivers-common' missing, assuming package has no files currently installed.

and:

dpkg: warning: files list file for package `brother-cups-wrapper-common' missing, assuming package has no files currently installed.

Can anyone tell me what to do about this?  I've checked Google, with no success.

Thanks, 

JimW

---

