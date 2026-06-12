---
title: "Brother Printer"
date: 2010-01-12
forum: Hardware
---

### Post by hooge1kanobi on 2010-01-12
Need help with an old Brother MFC8500.  I've followed several posts on the forums suggestions such as[COLOR=RoyalBlue]** [this one]("http://ubuntuforums.org/showthread.php?t=1306997&highlight=old+brother+printer")**[/COLOR] and other say following these[COLOR=RoyalBlue]** [instructions]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html") **[/COLOR]from Brother worked for them.  I've tried both but with no success.  I even tried to pull in the PPD from the install CD that came with the MFC8500.  I received the attached error report when trouble shooting. (sorry its 90Kb and exceeds the 19Kb limit, won't upload)

I'm a newbi to Linux/Ubuntu.  9.10 is my first install.  I'm finding my way arround and like it.  Just need help with a few tweaks like this one.;)

---

### Post by sgosnell on 2010-01-12
What doesn't work?  Won't print, won't scan, isn't recognized at all, what?  Is this a network or USB printer?  More detail, please.

With Brothers, I've always been able to just start with System/Administration/Printing, click on New, and have the printer recognized and installed.  The scankey tool and scanner driver are necessary in order to scan.

---

### Post by hooge1kanobi on 2010-01-13
Okay, I figured it out on my machine.  (The Printing, USB, - Not interested in using the Fax cuz the Scanner craped out a long time ago on this device.  Its a great B/W Laser Printer though.)  Like I said, I'm new to Ubuntu. Here is what I found worked.

Followed the instructions on [**This Page**]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html"):

 Pre-required Procedure (2)
    Related distributions
    Ubuntu8.04/8.04.1, Ubuntu8.10, Ubuntu9.04
    Related products/drivers
    cupswrapper printer/PC-FAX drivers
    Requirement
    1. "sudo aa-complain cupsd" command is required before the installation.
    2. "sudo mkdir /usr/share/cups/model" command (as it is) is required before the installation.

Moved on to [**this page**]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html").

Step 3. Download drivers
    Download LPR driver and cupswrapper driver.

(I hadn't tried both at the same time before)

   1. The "Cupswrapper"  .deb  &
   2. The "LPS"  .deb


Step 4. Install LPR driver and cupswrapper driver
    4-1. Turn on the printer and connect the USB cable.
    4-2. Open the terminal and go to the directory where the drivers are.
    4-3. Install LPR driver 

    Command (for dpkg)  :  dpkg  -i  --force-all  (lpr-drivername)

4-4. Install cupswrapper driver

Command (for dpkg)  :  dpkg  -i  --force-all  (cupswrapper-drivername)

4-5. Check if the LPR driver and cupswrapper driver are installed

    Command (for dpkg)  :  dpkg  -l  |  grep  Brother

Step 5a. (for USB Connection) Check your printer on the cups web interface
    5a-1. Open a web browser and go to "http://localhost:631/printers".

        Check if the Device URI of your printer is "usb://Brother/(your printer's model name)"

Step 6. Try a test print
    6-1. Open a text editor, write something and select "print" from the menu.

At this point I found 2 printers installed.  I think one was from an earlier try.  Any way one wouldn't print and the other one would.  I deleted the one that didn't work and I'm up and running!

Lesson learned.  Follow directions carefully!  Ubuntu may need multiple driver packages to make a USB printers work.

---

### Post by hooge1kanobi on 2010-01-13
> **sgosnell said:**
> What doesn't work?  Won't print, won't scan, isn't recognized at all, what?  Is this a network or USB printer?  More detail, please.

With Brothers, I've always been able to just start with System/Administration/Printing, click on New, and have the printer recognized and installed.  The scankey tool and scanner driver are necessary in order to scan.

Wasn't recogized by Ubuntu using the System/Administration/Printing - New - Recogize.  Ubuntu suggested a driver for a different model of MFC.  I tried it initially but test pages never went any where.

My connection type was USB local.

---

