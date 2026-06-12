---
title: "Dell A920: Driver Installed but Printer is a Paperweight"
date: 2007-08-07
forum: Hardware &amp; Laptops
---

### Post by RHorse on 2007-08-07
I have a Dell A920 and I installed the Lexmark Z600 CUPS driver upon reading these forums.  When I go to system, Printer Config, I see the printer detected at the USB port and I see the installed driver.  I associated the printer with the correct driver and now I was all set up.

The only problem is the printer absolutely does nothing.  Not a peep.  Even using a generic IBM compat dot matrix driver in printer setup, it does nothing.  It's funny, cuz using the same driver and printer it was working (though, with some flakiness) under Xandros, which is Debian based, also.  

I am leaning heavily toward some simple lil thing that I'm missing here, but don't know what to do next. 

*R* *H*

---

### Post by dchriscoe on 2007-08-07
I have a Lexmark Z611 (USB) that I just installed on Ubuntu 7.04.

It works fine but here is what you have to do:

First I assume that what I have read is correct: that the z600 driver will work with your Dell (equiv to Lexmark 1270). I downloaded the z600 package from the Lexmark site. The file CJLZ600LE-CUPS-1.0-1.TAR.gz was placed in my home folder.

Second I had to run Synaptic to install the alien program which converts rpm to deb. You may already have that program but make sure.

Now the long part, load the terminal and execute in the order below the following : Note when you "sudo alien" on the two files, ignore the warning messages.


$ tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz # extract the package
$ tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz # put the needed files into a tar file
$ tar -xvzf install.tar.gz # extract the tar file
$ sudo alien -i z600cups-1.0-1.i386.rpm # install the printer driver
$ sudo alien -i z600llpddk-2.0-1.i386.rpm # install misc. printer libraries
$ sudo /etc/init.d/cupsys restart # restart the cups daemon
$ /usr/lib/cups/backend/z600 # check that the printer backend works (You may get no output here but it works fine)


Go to System - Administration - Printing and choose the printer driver Z600 v1.0-1 under Lexmark (or, if it's not there, go to Install Driver and choose /usr/share/cups/model/Lexmark-Z600-lxz600cj-cups.ppd.gz).

For some resaon I had to install the printer twice. The first time the print driver above was not listed so I did the Install Driver. The printer did not work so I uninstalled it. On the second install the printer driver now appeared. I installed in this way and it now prints.

You will print OK but since the printer manager software for this machine is Windows based, the scan and copy button will probably not work
__________________

---

### Post by RHorse on 2007-08-08
> **dchriscoe said:**
> I have a Lexmark Z611 (USB) that I just installed on Ubuntu 7.04.

It works fine but here is what you have to do:

First I assume that what I have read is correct: that the z600 driver will work with your Dell (equiv to Lexmark 1270). I downloaded the z600 package from the Lexmark site. The file CJLZ600LE-CUPS-1.0-1.TAR.gz was placed in my home folder.

Second I had to run Synaptic to install the alien program which converts rpm to deb. You may already have that program but make sure.

Now the long part, load the terminal and execute in the order below the following : Note when you "sudo alien" on the two files, ignore the warning messages.


$ tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz # extract the package
$ tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz # put the needed files into a tar file
$ tar -xvzf install.tar.gz # extract the tar file
$ sudo alien -i z600cups-1.0-1.i386.rpm # install the printer driver
$ sudo alien -i z600llpddk-2.0-1.i386.rpm # install misc. printer libraries
$ sudo /etc/init.d/cupsys restart # restart the cups daemon
$ /usr/lib/cups/backend/z600 # check that the printer backend works (You may get no output here but it works fine)


Go to System - Administration - Printing and choose the printer driver Z600 v1.0-1 under Lexmark (or, if it's not there, go to Install Driver and choose /usr/share/cups/model/Lexmark-Z600-lxz600cj-cups.ppd.gz).

For some resaon I had to install the printer twice. The first time the print driver above was not listed so I did the Install Driver. The printer did not work so I uninstalled it. On the second install the printer driver now appeared. I installed in this way and it now prints.

You will print OK but since the printer manager software for this machine is Windows based, the scan and copy button will probably not work
__________________

Well, thanks for your advice.  I got it working.  My main problem was that I had done all that you said and I still could not get the printer to so much as hiccup.  The step I failed to take was to register it with the CUPS server.  So I went to [http://localhost:631](http://localhost:631) (the CUPS server) and clicked on Administration, and opened a New Printer dialog.  Then I registered the .pid file that came w/ the driver, and printed a test page: beautiful output.

Thanks for the helpful encouragement.

*R* *H*

---

### Post by vaskark on 2007-09-13
I have a Dell A920 printer too and want to get it working. I tried downloading the CJLZ600LE-CUPS-1.0-1.TAR.gz file from Lexmark but it's not available anymore. I tried google but all I get are links pointing to this nonexistent file (they state they are updating the site). Could someone post it here for me? I would really appreciate it.

Thanks.

---

