---
title: "Inability to use laser printer Canon LBP 2900 in 9.10"
date: 2009-11-01
forum: Hardware
---

### Post by Berk'n'Boni on 2009-11-01
I have a Canon LBP 2900 laser printer. I followed the recommended search window that opened when I first plugged it in but no results were forthcoming in either of the three options provided. Ubuntu doesn't recognise it.  The driver disc (presumably Windows/Mac) is unreadable.  I did a search on this site under the printer's name and found_**[ this possible solution]("https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900")**_ mentioned in a post. Whilst for an older version of the OS I followed the instructions very carefully.  It failed to work.

Neither of the driver packages mentioned (1.60 and 1.80) would install and gave irreconcilable error messages.

Is there a valid solution?  And/or is the LBP2900 ever going to be added to the printer database? (Not being able to use an expensive printer less than a year old would be a major point against this OS for me.)

Thank you kindly for any help anyone is able to give.


-- Completely new Ubuntu user. Very unfamiliar with Ubuntu's design and file structure, but have been persevering the past three days with various problems.  Would like to end up using this permanently but if problems persist in surfacing I suspect there'll be a cut-off point sometime.

---

### Post by itsmine on 2009-11-03
The same as yours!

---

### Post by werecatomega on 2009-11-03
i've found a site that claims it has the drivers.

[http://driverscollection.com/?H=LBP2900&By=Canon&SS=Linux](http://driverscollection.com/?H=LBP2900&By=Canon&SS=Linux)

i'm not sure if the driver works because i don't have that printer, but you might want to give it a try

---

### Post by RonaldP3 on 2009-11-10
Hi,

After quite some effort I got my lbp2900 to work under Jaunty. You have to follow the instructions at: [https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900)

Do step 1 through 9 AND the "[SIZE=1]Automatically reporting errors[/SIZE]" section. You need to make files and move them around using the terminal. Help for using the terminal you can find here: [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal).

At my computer the file you need to make at step 5 only worked when I started the first line with: #! /bin/sh

If the files you made are not working at some point it is worth checking if you need to replace "cupsys" with "cups" somewhere in the text.

Good luck!

---

### Post by kdmitriyval on 2010-02-17
I have the same problem in this case
I did everything what described this link: [https://help.ubuntu.com/community/CanonCaptDrv190](https://help.ubuntu.com/community/CanonCaptDrv190), but my printer didn't start working. When I turn it on, Ubuntu 9.10 recognizes it. Next I try to print test page or something else, the system shows me a message "Test page submitted as job No" and printer does nothing. 
What should I do? Please help me with my problem.

P.S.: I'm Linux beginner user, but I'd like to use it for everyday tasks like windows.

---

### Post by kdmitriyval on 2010-02-17
I DID IT!!!!:))))

I removed all drivers, next I downloaded printer drivers ver 1.80 from Canon web site and installed packages. After that, I turned on printer and went to its property. Found device URI and chose Canon Printer Daemon Port #1. Next I found in the textbox of device URI the line "ccp:/var/ccpd/fifo0". After, I started Terminal and put this command: sudo gedit /etc/ccpd.conf where I found following lines and little bit correct them:

#<Printer LBP3200>
#DevicePath /dev/usb/lp0
#</Printer>

So, the sign # must be deleted in all 3 lines and the figure **3200** must be changed into **2900.** Also I deleted sign "/" between usb and lp0 in second line -> DevicePath /dev/**usblp0**
Next I tried to restart ccpd service (sudo /ect/init.d/ccpd restart), but linux said to me that it didn't know this command. That's why I restarted Linux. When I did it, I tried again to restart ccpd service, but it wrote me same message. Then I checked the print working with command: captstatusui -P LBP2900. I got a window od my printer status, then I went again to printer property and print test page without any problem. 

Next I made some things for automatically start print service: so I wrote command: sudo gedit /etc/rc.local and added this line: /etc/init.d/ccpd restart

*source: some Russian forums*

---

### Post by netlaptop on 2010-03-17
Does anyone make this printer works on Ubuntu 9.10 64 bits?

---

