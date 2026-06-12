---
title: "Installing Samsung Mono Laser Printer into Ubuntu 12.04"
date: 2014-04-06
forum: Hardware
---

### Post by pauloz on 2014-04-06
Greetings. I've tried to install my new Samsung Mono Laser Printer SCX-3405FW into Ubuntu 12.04 but I'm having issues getting full functionality. My machine dual boots with Windows 7 and there were no problems installing in Windows. I had no problems going into System Settings and adding the printer there, but it only has basic functionality there - I can't scan at all or do double sided printing. I tried a couple of scanning apps (Simple Scan and XSane) but they don't recognise the device at all. 

I decided to download the 3 files (driver, smart panel & printer setting utility) available on the Samsung website ([http://www.samsung.com/au/support/model/SCX-3405FW/XSA-downloads](http://www.samsung.com/au/support/model/SCX-3405FW/XSA-downloads)) for Linux OS. This is why I chose the Samsung because it's compatible with Linux, unlike other printers. All three are tar.gz files and I had no problems extracting them. However, the problems start at the next step. Two folders are extracted - the Unified Linux Driver folder and cdroot folder. For the ULD folder, Samsung's instructions are to click cdroot > autorun then a Welcome screen is supposed to appear. There is no such option available. With the cdroot folder, the instructions are cdroot > Linux > smartpanel (or psu) > install.sh. When I click "install.sh" a message displays whether I want to run "install.sh" (an executable text file) or display its contents. The options given are:

1. Run in Terminal
Selecting this, the Terminal screen flickers on momentarily then disappears.
2. Display
Selecting this, a message appears 'Could not open "install.sh" - archive type not supported'.
3. Run
Selecting this, nothing happens.

I use Ubuntu about 80% of the time (dislike Windows) and look forward to any assistance. I would appreciate step by step instructions - I'm definitely no expert! Thanks.

---

### Post by pdc on 2014-04-07
so the file comes down as [COLOR="#008000"]ULD_V1.00.21.tar.gz[/COLOR]

I think the commands in a terminal would be 

> [COLOR="#FF0000"]cd Downloads[/COLOR]

> [COLOR="#FF0000"]tar -xzvf ULD_V1.00.21.tar.gz[/COLOR]

..........the command [COLOR="#FF0000"]ls[/COLOR] shows that the above command creates a directory called [COLOR="#0000FF"]uld[/COLOR] .........so next command is 

> [COLOR="#FF0000"]cd uld[/COLOR]

the command to list what is in that directory is > [COLOR="#FF0000"]ls[/COLOR] and that gives 

> [COLOR="#008000"]arm   install-printer.sh  install.sh  uninstall-printer.sh  uninstall.sh
i386  install-scanner.sh  noarch      uninstall-scanner.sh  x86_64[/COLOR] 

and I believe the command to install the printer would be 

> [COLOR="#FF0000"]./install-printer.sh[/COLOR] and to install the scanner would be > [COLOR="#FF0000"]./install-scanner.sh[/COLOR]

---

### Post by pauloz on 2014-04-08
Thanks for your help pdc - really appreciate it. I've managed to get the scanner working (after your suggestion) but still can't print double-sided. I installed all 3 files downloaded from the Samsung website, however the Samsung Smart Panel does not open. I think I may have to grin and bear the fact I won't have full functionality like I do in Windows. I'm still working my way around trying to set up the wireless connection.

---

### Post by pdc on 2014-04-08
If I type Alt-F2 I get a command line and if I type in > [COLOR="#FF0000"]system-config-printer[/COLOR] it opens up the printer folder; if I right click on our MG3100 that will print duplex, there is a dialogue box opens where I can set the duplex option; 

for libreoffice, if I paste > [COLOR="#FF0000"]/usr/lib/libreoffice/program/spadmin[/COLOR], I get a dialogue box to alter settings in libreoffice (thumbnail enclosed is called spadmin.png)

any help? ...I guess 64bit systems may well be */usr/lib64/libreoffice/program/spadmin*

---

### Post by pauloz on 2014-04-09
When I typed "system-config-printer" the printer folder opened up but it had the following message:    (process:9243): Gtk-WARNING **: Locale not supported by C library. Using the fallback 'C' locale. 
No luck with LibreOffice - I got the message "No such file or directory".
I guess if I want to use the two-sided function, I'll have to switch over to Windows. Thanks anyway.

---

