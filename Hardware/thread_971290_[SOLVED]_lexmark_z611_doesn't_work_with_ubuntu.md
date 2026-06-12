---
title: "[SOLVED] lexmark z611 doesn't work with ubuntu"
date: 2008-11-04
forum: Hardware
---

### Post by banana jama on 2008-11-04
i have a lexmark z611 printer and im using ubuntu 8.10 (upgraded from 8.04) ubuntu recognizes the printer and says that it install the driver but when i try to print a document in openoffice.0rg 3.0 open office says an error while printing. its not just open office either it doesn't work when i try to print a picture off the internet. can anyone help? i hate having to use microsoft to print a document (printing stuff is the only reason microsoft is still on my laptop).


[SIZE="4"][COLOR="Red"]update march 6 2009: go to my (bananajama) last post steps have been added to setup printer[/COLOR][/SIZE]

---

### Post by banana jama on 2008-11-23
i solved the problem. if you have the same problem do the following:

*if you already pluged in your lexmark z611 printer and it doesn't work to to system---> administrator----> printing 
*your printer will come up on the screen
*right click it and press delete
*unplug the printer
*replug the printer
*on the top panel an notification box will show saying "a generic driver been installed" you'll also see an option called find driver
*click on find driver 
*scroll down to lexmark
*find z500-600 (it should be the last one on the list)
*a new box will pop up
*chose new PPD (this will ensure that the new driver will start automatically)
* to make sure it works click on test print a sheet with ubuntu should print.

i hope this helps im not a computer genius so i can't give instructions any clearer than this.


[SIZE="4"][COLOR="Red"]update march 6 2009: go to my (bananajama) last post steps have been added to setup printer[/COLOR][/SIZE]

---

### Post by Micy on 2008-11-29
> find z500-600 (it should be the last one on the list)
I cann not find any z600 or z500 on the list.

What shall I do now because my printer (Z612) still refuse to print.

Thank you for your answers and help!

---

### Post by pwebster25 on 2008-11-29
> **banana jama said:**
> i solved the problem. if you have the same problem do the following:

*if you already pluged in your lexmark z611 printer and it doesn't work to to system---> administrator----> printing 
*your printer will come up on the screen
*right click it and press delete
*unplug the printer
*replug the printer
*on the top panel an notification box will show saying "a generic driver been installed" you'll also see an option called find driver
*click on find driver 
*scroll down to lexmark
*find z500-600 (it should be the last one on the list)
*a new box will pop up
*chose new PPD (this will ensure that the new driver will start automatically)
* to make sure it works click on test print a sheet with ubuntu should print.

i hope this helps im not a computer genius so i can't give instructions any clearer than this.


I had hopes this might help solve my problem with my Lexmark X6150 in Intrepid.  In the unanswered thread at [http://ubuntuforums.org/showthread.php?t=976005](http://ubuntuforums.org/showthread.php?t=976005) I describe what I tried.  I also tried following your directions.  I chose the nearest default that was available (z53 instead of the recommended z55).  When I did this per instructions in this thread, I get a blank paper to run through once when doing a test print but from then on it says the printer is not connected.
Any recommendations anyone?

---

### Post by cognus on 2008-11-30
Try this page:  [http://onlyubuntu.blogspot.com/2008/06/howto-setup-lexmark-z611-printer-in.html](http://onlyubuntu.blogspot.com/2008/06/howto-setup-lexmark-z611-printer-in.html)  It worked for me!

Being a n00b myself, I really liked the comments explaining what each step is in the process.

---

### Post by banana jama on 2009-03-06
download the lexmark driver at this site [http://downloads.lexmark.com/perl/downloads/downloads.cgi]("http://downloads.lexmark.com/perl/downloads/downloads.cgi")

[COLOR="Red"][SIZE="4"]NOTE: SAVE FILE IN HOME FOLDER NOT DESKTOP MAKES THINGS EASIER[/SIZE][/COLOR]

then follwed these instructions i got it off of this website [http://onlyubuntu.blogspot.com/2008/06/howto-setup-lexmark-z611-printer-in.html]("http://onlyubuntu.blogspot.com/2008/06/howto-setup-lexmark-z611-printer-in.html")


> Step 1: Install Supporting Packages

sudo apt-get install alien libstdc++5

Yes, you want to install that specific version of libstdc, even if you have a newer version.

Step 2: Activate the USB Filesystem

It was necessary to add the following line to /etc/fstab in order to get this working.

usbfs /proc/bus/usb usbfs devgid=14 0 0

Then you'll want to mount the USB Filesystem

sudo mount usbfs

Step 3: Download Driver from Lexmark

You will want to grab the Red Hat Linux driver for the Z611, which should be named CJLZ600LE-CUPS-1.0-1.TAR.gz. I would recommend creating a folder somewhere and download this file into that folder.

Step 4: Extract and Install the Driver

Execute the following commands exactly as listed, no modifications or tweaks should be necessary for the average user. (You don't need to execute the comment lines however)

## Extracting the driver
tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz

## The shell script doesn't work out of the box
tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz

## Extracting the contents from the above command
tar -xvzf install.tar.gz

## Convert RPM to TGZ (alien may complain about --scripts not being used, you can ignore that warning)
sudo alien -t z600cups-1.0-1.i386.rpm

## Convert RPM to TGZ (alien may complain about --scripts not being used, you can ignore that warning)
sudo alien -t z600llpddk-2.0-1.i386.rpm

## Extracting the contents of the TGZ into the appropriate locations
sudo tar xvzf z600llpddk-2.0.tgz -C /

## Extracting the contents of the TGZ into the appropriate locations
sudo tar xvzf z600cups-1.0.tgz -C /

## Tell Ubuntu to refresh to see the new libraries
sudo ldconfig

## Move to location of PPDs
cd /usr/share/cups/model

## gunzip the PPD
sudo gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz

## The driver installation is now complete, restart cupsys
sudo /etc/init.d/cupsys restart

Step 5: Activate Printer and Driver

Execute the following command

/usr/lib/cups/backend/z600

If all is well you should see something similar to the following:

user@hostname:/usr/share/cups/model$ /usr/lib/cups/backend/z600
direct z600:/dev/usb/lp0 "Lexmark Lexmark Z600 Series" " Lexmark Printer"

If that doesn't work, check to see if usbfs is listed in 'cat /proc/mounts'.

Step 6: Setup Printer

If you are using GNOME:

1. Click on System -> Administration -> Printing
2. Click 'New Printer'
3. Select 'Lexmark Printer' from the list, which should have something like 'z600:/dev/usb/lp0' for Device URI. Click Forward.
4. Select 'Lexmark' from the manufacturer list and click Forward.
5. Click on 'Z600' in the model list. Driver should show as 'Lexmark Z600 v1.0-1'
6. Setup your preferred Printer Name, Description and Location and click Apply

At this point you should have a working printer 

hopes this solves people's problem with this lexmark printer model.

---

### Post by suncoup on 2010-01-28
Hey Banana Jama, thanks! My wife's happy that our old hand-me-down lexmark is now working. Awesome.

---

