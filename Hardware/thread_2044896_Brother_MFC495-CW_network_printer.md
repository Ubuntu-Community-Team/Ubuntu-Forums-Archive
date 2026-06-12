---
title: "Brother MFC495-CW network printer"
date: 2012-08-20
forum: Hardware
---

### Post by SailBlue5 on 2012-08-20
Hi,

I have seen a few other posts about getting this printer to work in Ubuntu but following the advice there and the instructions from Brother's website I haven't been able to print anything.  I followed the CUPS instructions from:
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)
and when installing the drivers I made directories needed so that the drivers installed.
Now under printing I see the MFC495CW however if I print to it from a text editor jobs will show up in the queue and stay there forever as processing. If I do a test page from the properties menu it shows up for a brief second and disappears in the queue. Nothing ever prints. Under properties for the printer I have
Device URI: lpd://192.168.1.7/binary_p1
Make and Model: Brother MFC-495CW CUPS
and it always says idel.

The printer is hooked up via an ethernet cable and has a IP of 192.168.1.7 that I can ping.

Thanks for the help.

---

### Post by gifford on 2012-08-20
I have the same printer and have never had an installation problem. It is also set up on the network and works on wireless and Ethernet.

Give some more specifics on how you installed the drivers. Did you follow the latest instructions? Are you using Ubuntu 12.04?

One quick attempt to solve would be going to printer settings and delete the printer and then scan for new network printer. There have been occasions that the printer is set up as usb attached and not network.

As I see it is already listed as a network printer..go ahead and delete the current listed printer, then scan for network printer and you should be given several options for listed printers and protocol. Try selecting the one with settings different from what you selected before and see if it will print for you.

Otherwise, the only advice I can give is to re install the drivers again following the instructions on the Brother site. Good luck.

---

### Post by SailBlue5 on 2012-08-20
I am using Ubuntu 12.04, 64-bit.  I tried to delete the printer and using the add in the printing window, I also deleted that one and tried the brother install from the command line and then configure the printer in the CUPS web interface (as indicated in the brother install). Below is the terminal from that, maybe it will show something a more experienced person will pick up on.
I do get a "lpadmin: The printer or class does not exist." but it didn't seem to hinder the rest of the install.


mrherman@Lithium:~/Downloads$ sudo dpkg -i --force-all mfc495cwlpr-1.1.3-1.i386.deb
[sudo] password for mrherman: 
(Reading database ... 201539 files and directories currently installed.)
Preparing to replace mfc495cwlpr:i386 1.1.3-1 (using mfc495cwlpr-1.1.3-1.i386.deb) ...
Unpacking replacement mfc495cwlpr:i386 ...
Setting up mfc495cwlpr:i386 (1.1.3-1) ...
mrherman@Lithium:~/Downloads$ sudo dpkg -i --force-all mfc495cwcupswrapper-1.1.3-1.i386.deb
(Reading database ... 201539 files and directories currently installed.)
Preparing to replace mfc495cwcupswrapper:i386 1.1.3-1 (using mfc495cwcupswrapper-1.1.3-1.i386.deb) ...
lpadmin: The printer or class does not exist.
cups stop/waiting
cups start/running, process 2771
Unpacking replacement mfc495cwcupswrapper:i386 ...
Setting up mfc495cwcupswrapper:i386 (1.1.3-1) ...
cups stop/waiting
cups start/running, process 2863
mrherman@Lithium:~/Downloads$ sudo dpkg -l |grep Brother
ii  mfc495cwcupswrapper:i386               1.1.3-1                                 Brother CUPS Inkjet Printer Definitions
ii  mfc495cwlpr:i386                       1.1.3-1                                 Brother lpr Inkjet Printer Definitions
ii  printer-driver-ptouch                  1.3-3ubuntu0.1                          printer driver Brother P-touch label printers

---

### Post by SailBlue5 on 2012-08-20
Thanks for the help, looking at the Brother's install guide that I linked above I realized I didn't check "Check if pre-required procedures are completed" in step 2.  After doing this the and re-adding the printer I got the printer working.

Thanks to everyone for the help.

---

### Post by kurt18947 on 2012-08-20
Here is a post of mine - see #4.  Brother's installer script has worked very well for me.  When it asks if you want to specify the connection, you do.  The default is a USB connection.  If you can, I'd recommend assigning the machine a static I.P. address.  I've found HP Jet Direct/ socket:  network connection to be most reliable.  Getting the scanner to work especially on 64 bit installs can take some patience.

[http://ubuntuforums.org/showthread.php?t=1999216&highlight=brother](http://ubuntuforums.org/showthread.php?t=1999216&highlight=brother)

---

