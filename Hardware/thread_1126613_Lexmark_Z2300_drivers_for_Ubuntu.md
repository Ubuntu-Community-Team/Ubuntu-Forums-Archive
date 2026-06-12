---
title: "Lexmark Z2300 drivers for Ubuntu?"
date: 2009-04-15
forum: Hardware
---

### Post by berrypievision on 2009-04-15
I've checked Linuxprinting org and couldn't find the drivers.  Does anyone know where I can download them?

---

### Post by berrypievision on 2009-04-16
Anyone know where I can download the drivers?

---

### Post by Daisuke_Aramaki on 2009-04-16
> **berrypievision said:**
> Anyone know where I can download the drivers?

Looks like there are no linux drivers available for this printer. and foomatic doesn't include it as well.

Anyway refer these documents for more!

[http://openprinting.org/show_printer.cgi?recnum=Lexmark-2300series]("http://openprinting.org/show_printer.cgi?recnum=Lexmark-2300series")

[http://forums.linux-foundation.org/read.php?29,6729]("http://forums.linux-foundation.org/read.php?29,6729")

---

### Post by klyick on 2009-04-20
I also am looking for this driver, because apparently Lexmark decided that they were going to take down these drivers. 

I can't seem to get this printer to work under Ubuntu, can anyone help?

---

### Post by segnini75 on 2009-05-22
I ve done a solution for the z2300 lexmark printer in linux , its on [http://veneideas.com/Lexmark_z2300_linux_x86_64.html](http://veneideas.com/Lexmark_z2300_linux_x86_64.html)

works fine for me in 64 bits but would work on 32 bit too.

---

### Post by nerdzero on 2009-07-29
In case someone comes across this later, I was able to get my Z2300 working on 9.04 with Lexmark's driver.

[http://downloads.lexmark.com/perl/downloads/downloads.cgi](http://downloads.lexmark.com/perl/downloads/downloads.cgi)

Enter country, language, etc.  Search by model number and enter Z2300.  Choose Ubuntu 8.04 LTS from the dropdown menu and it will let you download a zipped script.  It says it's for 8.04 but it worked for me on 9.04 as well.

Unplug the printer, run the script (you don't have to run with sudo since it will prompt for your password later), follow the wizard, and then plug in when instructed to.  Make sure it's powered on before you plug it in.

When you plug it in, Ubuntu will create a printer for you. It may take a sec but wait for that to happen before clicking Next. Delete that one and then finish the wizard.  Lexmark's script will also create a printer for you at this point.  Set that one as your default.  The script will also add a utility to your Administration menu to let you check ink levels.

---

### Post by mciancio on 2009-09-10
Download it from 

[http://www.downloaddelivery.com/downloads/cpd/lexmark-inkjet-08-driver-1.0-1.i386.deb.sh.zip](http://www.downloaddelivery.com/downloads/cpd/lexmark-inkjet-08-driver-1.0-1.i386.deb.sh.zip)

unzip, start and then, if it stops (like in my case), kill -9 it.
In the same dir you'll find a directory like this "selfgz18929/pkg/files"
inside which there is lexmark-inkjet-08-driver-1.0-1.i386.deb.

Install it and go.

And the next printer will be HP....

---

### Post by Evilthrill on 2010-04-28
> **mciancio said:**
> Download it from 

[http://www.downloaddelivery.com/downloads/cpd/lexmark-inkjet-08-driver-1.0-1.i386.deb.sh.zip](http://www.downloaddelivery.com/downloads/cpd/lexmark-inkjet-08-driver-1.0-1.i386.deb.sh.zip)

unzip, start and then, if it stops (like in my case), kill -9 it.
In the same dir you'll find a directory like this "selfgz18929/pkg/files"
inside which there is lexmark-inkjet-08-driver-1.0-1.i386.deb.

Install it and go.

And the next printer will be HP....

How come there is administrative password needed??
anyone can help me??
I thought it is comp password,but it isn't...

---

### Post by 2hot6ft2 on 2010-04-28
> **Evilthrill said:**
> How come there is administrative password needed??
anyone can help me??
I thought it is comp password,but it isn't...
Considering that post that had that link is from last September and the poster has only made 4 posts total I wouldn't even try it with that.

You should get the driver from the lexmark site and follow their instructions for installing it.

[Installer Package for Systems using Debian-based packaging system.]("http://support.lexmark.com/index?page=content&actp=DD_LIST&productCode=LEXMARK_Z2300&id=DR860&os=UBUNTU_8_04_LTS&oslocale=en_US&segment=DOWNLOAD&userlocale=EN_US+&locale=en")

[http://support.lexmark.com/index?page=content&id=OS4&locale=EN&userlocale=EN_US](http://support.lexmark.com/index?page=content&id=OS4&locale=EN&userlocale=EN_US)

```
DEB-based distros:    
   
    # ./lexmark-inkjet-[xx]-driver-1.0-1.i386.deb.sh
   
4. Follow the instruction in the installation screen.     
   
B. By double-clicking the script file:    
   
1. Extract the zip file.    
2. Double-click the script file.   
3. Click Run in Terminal button to run the installer.   
4. Follow the instruction in the installation screen.

```

---

### Post by Evilthrill on 2010-04-29
> **2hot6ft2 said:**
> Considering that post that had that link is from last September and the poster has only made 4 posts total I wouldn't even try it with that.

You should get the driver from the lexmark site and follow their instructions for installing it.

[Installer Package for Systems using Debian-based packaging system.]("http://support.lexmark.com/index?page=content&actp=DD_LIST&productCode=LEXMARK_Z2300&id=DR860&os=UBUNTU_8_04_LTS&oslocale=en_US&segment=DOWNLOAD&userlocale=EN_US+&locale=en")

[http://support.lexmark.com/index?page=content&id=OS4&locale=EN&userlocale=EN_US](http://support.lexmark.com/index?page=content&id=OS4&locale=EN&userlocale=EN_US)

```
DEB-based distros:    
   
    # ./lexmark-inkjet-[xx]-driver-1.0-1.i386.deb.sh
   
4. Follow the instruction in the installation screen.     
   
B. By double-clicking the script file:    
   
1. Extract the zip file.    
2. Double-click the script file.   
3. Click Run in Terminal button to run the installer.   
4. Follow the instruction in the installation screen.

```

it want me to insert the password..You try install it..Then u know..

---

### Post by JWDuncan on 2011-01-29
My root Administrator password will not work with ANY LEXMARK downloaded driver. 
I see other people have had the same problem and are not getting any answers either.

I've never encountered any other download installation that requires a root password other than the one I personally set on my machine as the administrator when I installed Unbuntu in any version.

Lexmark Printer drivers that claim to work, I'll never know since I can't get past the root password screen it is looking for. 

Two different printers and supposedly working drivers, including the ones listed here, have the exact same problem.

Contacting Lexmark technical support via email has been completely useless. I'll try to get them on the telephone today and hope to find a solution. Otherwise, this printer goes back also, and no more Lexmark printers ever!

I need the thing to work, not lame excuses.

Those of you that found the drivers and got them to work, how did you get past the root password when installing in terminal mode when it does not match your own that you entered when you installed Linux?

This is what I need to know, not where to get the download file. I have it, extracted it, and it will not install from the shell script without the root password the software thinks it should be.

---

### Post by nerdzero on 2011-01-29
Try: ```
sudo -i
``` Enter your password when prompted.  This will put you in a root console.  Then execute the script from lexmark.  It shouldn't prompt you for your password this time because you are already executing as "root".

I think the reason it doesn't work as a non-admin is because they are actually trying to swith to the root user which is effectively disabled in Ubuntu.

---

### Post by 3ruce on 2011-03-01
> **JWDuncan said:**
> This is what I need to know, not where to get the download file. I have it, extracted it, and it will not install from the shell script without the root password the software thinks it should be.

This [page]("https://help.ubuntu.com/community/RootSudo") sorted the root problem out, but the Lexmark driver installation program doesn't see it connected to the machine, even though Ubuntu itself searches for drivers!!! At this this has been my experience so far :-(

Have you had any joy?

---

### Post by Dalkorian on 2012-01-11
I'm having a demonic time trying to get my Lexmark Z2300 working in Kubuntu and I'm hoping someone has a trick for me to try. Here's where I am now ...

I grabbed the printer drivers from Lexmark at the following URL:
[http://support.lexmark.com/index?productCode=LEXMARK_Z2300&segment=DOWNLOAD&os=UBUNTU_8_04_LTS&oslocale=en_US&page=content&actp=DD_LIST&id=DR860&locale=en&userlocale=EN_US](http://support.lexmark.com/index?productCode=LEXMARK_Z2300&segment=DOWNLOAD&os=UBUNTU_8_04_LTS&oslocale=en_US&page=content&actp=DD_LIST&id=DR860&locale=en&userlocale=EN_US)

Tried installing via terminal, only found a bunch of errors regarding "no protocol specified", "screen for GtkWindow not set", some PANGO-CRITICAL errors and ending off with a floating point exception. No love there.

I next tried simply clicking on the installer in the GUI, which prompted me for a root password. That was a hang-up for a while until I realized I needed to first activate the root account, then that went swimmingly ... up to a point. It's when the installer asks me to plug in the printer that it seems to hang indefinitely. Clicking Next prompts me again and again to plug the printer into the USB port, even though I've done that. I just can't get past this part.

The result of all this is a printer that shows up in System Settings -> Printer Configuration, but won't print a test page (job shows up in queue, but is immediately stopped - User, Document and Time Submitted all show as Unknown). 

Any ideas where to go from here?

---

### Post by oCan on 2012-02-28
The model number **Lexmark Z2300 Printer** does not seem to be correct.

**Method 1:**
You may refer to the below links and use the troubleshooters. Check if it lists and helps resolve any issues: Open the Printer troubleshooter:
[http://support.lexmark.com/index?page=content&productCode=LEXMARK_Z2300&actp=PRODUCT&id=DR13284&segment=SUPPORT&userlocale=EN_US&locale=en](http://support.lexmark.com/index?page=content&productCode=LEXMARK_Z2300&actp=PRODUCT&id=DR13284&segment=SUPPORT&userlocale=EN_US&locale=en)

**Method 2: **
You may check if you have the latest drivers installed for the device. You may refer to the below link for getting the latest drivers and check –
[Lexmark Z2300 Driver]("http://www.lexmarkdrivers.net/inkjet-printers/lexmark-z2300-driver.html")

Good Luck.

---

