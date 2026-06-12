---
title: "User Authentication with Konica Minolta Bizhub (c364 and similar)"
date: 2015-08-28
forum: Hardware
---

### Post by Wanganui on 2015-08-28
Our school uses User Authentication (not to be confused with Account Tracking) on the Konica Minolta C364 printer. (Credit goes to this post for helping me figure this out: [http://forums.linuxmint.com/viewtopic.php?f=49&t=41244#p357622](http://forums.linuxmint.com/viewtopic.php?f=49&t=41244#p357622))

This is an outline of what I had to do to get User Authentication working on my Ubuntu 14.04.3 machine with the Konica Minolta c364

**Step 1**: Prepare the PPD driver.

Download the PPD driver file from the Konica Minolta website.  Place it in /usr/share/ppd/custom. Go in with an editor and modify this file. Add a line near the beginning of the PPD file to call a filter (that we will create in a moment). The line to add is just a few lines down and starts with "*cupsFilter..." The beginning of mine looks like this: (The line in bold is what I added).

```
*PPD-Adobe: "4.3"
*FormatVersion: "4.3"
*LanguageVersion: English
*LanguageEncoding: ISOLatin1
*FileVersion: "20000.0000"
*% Linux Version

***cupsFilter:	"application/vnd.cups-postscript 0 minolta"**

*Manufacturer: "KONICA MINOLTA"
*ModelName: "KONICA MINOLTA C364SeriesPS/P"
*ShortNickName: "KONICA MINOLTA C364"
*NickName: "KONICA MINOLTA C364SeriesPS(P)"
*PCFileName: "KOC364UX.ppd"
```
 

**Step 2**:  Install the printer with the PPD driver in CUPS. (The device URI might look something like this : ipp://192.168.1.100:631/ipp - but this will obviously vary with your setup.) When it comes time to choose the PPD file, my installation actually skipped the step and automatically grabbed the file I already placed in /usr/share/ppd/custom.  If your system doesn't grab it automatically, select it manually.  Once the installation is complete you may wish to run a little test: if the printer is correctly installed, when you send a print job (without authentication at this point. of course) you can go into the Job History on the Konica Minolta and see the job, "Deleted Due to Error", and the detail will say "Login Error".  The point of this test is to ensure that you do have some basic connectivity / communication with the printer, and that the only remaining problem to solve is the authentication.


**Step 3**: Create a filter file.

I used the info from the link above to create a filter file called "minolta" in /usr/lib/cups/filter.  Mine looks as below: (modified a bit from the link referenced above to use "User Authentication" instead of "Account Tracking"). Once the file is created, use "chmod 755 minolta" to give it execute permissions.

```
#!/bin/bash

source /etc/cups/ppd/${PRINTER}.km

echo -en "\033%-12345X"
echo -en "@PJL JOB\015\012"
echo -en "@PJL SET KMUSERNAME = \"${ACCOUNT_NAME}\"\015\012"
echo -en "@PJL SET KMUSERKEY2 = \"${ACCOUNT_PASSWORD}\"\015\012"
echo -en "@PJL SET KMCOETYPE = ${ACCOUNT_COETYPE}\015\012"
echo -en "@PJL ENTER LANGUAGE = POSTSCRIPT\015\012"

cat -

echo -en "\004\033%-12345X\015\012@PJL EOJ\015\012"
echo -en "\033%-12345X"
```

**Step 4**: Create a text file with the variables for the filter to reference.  This file should be in /etc/cups/ppd, and should have the same filename as the ppd file being used for printing, but with the extension ".km" instead of ".ppd".  (When you finished the installation in step 2, CUPS made a "working copy" for itself of your PPD file in /etc/cups/ppd. In that same directory, create this text file, copying the name exactly, except for the ".km") Mine looks like this:

```
ACCOUNT_NAME="admin2"
ACCOUNT_PASSWORD="3104"
ACCOUNT_COETYPE="0"
```

In the example above, admin2 is my username on the Konica Minolta, and 3104 is my password. The "coetype" variable needs to be set to 2 if the passcode is encrypted, and to 0 if it is not.  (If you do a print capture from a Windows machine, as I did in solving this riddle, you'll see that the windows driver encrypts the password, and thus the "coetype" is 2.)

**Step 5**: Restart CUPS : "service cups restart".  Now you should be able to go into any program and print something off.

Hopefully that does it for you!  It took me a lot of pain and tears to get this working, so I hope this helps someone!

*Known issues: This method is going to send the same username and password to the printer regardless of which Ubuntu user is logged in, because we put the username and password reference into the filter that is always run as root, and references the .km file as root.*

---

### Post by arauzo on 2016-02-08
Working on bizhub C253, using the PPD installed by default in Ubuntu 15.4. I had to change the script to KMSECTION instead (as in the link mentioned at the start of the page. I did not know if mine was account tracking or user identification so I tried both).

Thank you very much!! :-)

---

### Post by chris240 on 2016-05-25
Hello 

Thanks for the post work nice but i have small error got 2 the same printers both print but one works with my finger and then the other printer just print don't know why its doing this any suggestions?

Thanks.

---

