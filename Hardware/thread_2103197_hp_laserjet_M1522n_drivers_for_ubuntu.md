---
title: "hp laserjet M1522n drivers for ubuntu"
date: 2013-01-09
forum: Hardware
---

### Post by damianos t on 2013-01-09
I have installed the latest version of ubuntu, but I cannot use it because I cannot install drivers for my mfp hp.
I have downloaded a file, but it does not work because it says that some command is wrong... 
Has anyone used drivers for this hp product? 
thanks in advance.
Damianos

---

### Post by John_Swing on 2013-01-09
Hello,

[Hplip]("http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_m1522nf_mfp.html") (HP Linux Imaging and Printing) seems to support your printer. You can install it easily with the software-center, search for hplip-gui
Then open hplip with the dash and follow the instructions.

Regards.

---

### Post by Frogs Hair on 2013-01-09
The HPLIP GUI is nice for multi-function / all in one printers, but when you open printers and select add Ubuntu should search for a driver automatically after locating the printer.

---

### Post by damianos t on 2013-01-11
I have downloaded the file hplip-3.12.11.run
I ran it from the dash and the result was:

There was a problem opening the file home/ .../hplip-3.12.11.run
the file you opened has some invalid characters 
if you continue editing you could corrupt this document
you can also choose another character encoding and try again
character encoding : UTF-8
I also tried the western ISO -8859-15

but the message is the same.

Any ideas?

---

### Post by John_Swing on 2013-01-11
Hello,

I assume you are new to Ubuntu and coming from Windows.

Rather than leaving it up to the user to track down installer files and keep applications updated, Ubuntu (like many other Linux distributions) has a software package management system that provides a searchable database of easily installable applications (like an online shopping cart but the software is cost-free), which it will download and install for you with a few clicks.

In your case, rather than downloading hplip-3.12.11.run, open the software center, search for hplip toolbox, click on install.

But like said in the post above, maybe you don't even need to install hplip : search for "printers" in the dash, click on add, select your printer and it should automatically find a driver.

Regards.

---

### Post by damianos t on 2013-01-11
I had already done that, dash / printers/ and then my printer appears but with a "i", meaning not connected. 
I unplugged it, but nothing
I turned off the printer and reopened it, but nothing.
it does not print the text page.
I opened the que, but says not connected.

---

### Post by John_Swing on 2013-01-11
Even with Hplip ?

---

### Post by iMac71 on 2013-01-11
I post also here the answer I give in your other post: try to download the driver from the following link:
[http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareIndex.jsp?lang=en&cc=it&prodNameId=3442751&prodTypeId=18972&prodSeriesId=3442750&swEnvOID=2020&taskId=135&swLang=8](http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareIndex.jsp?lang=en&cc=it&prodNameId=3442751&prodTypeId=18972&prodSeriesId=3442750&swEnvOID=2020&taskId=135&swLang=8)

---

### Post by Yetisaurus Akjas on 2013-01-11
Try running "hp-setup" and "hp-check" from the command line (the terminal opens pressing Alt-F2, writing "xterm" in the line that appears and pressing Enter. 

Or you can look for the file named "hplip.conf" in /etc/hp/ (write "locate hplip.conf" in the terminal).  

You could find out if you have hplip installed by (and what version) by running "dpkg -l | grep hplip" in the terminal. 

If the printer is connected via USB, run "lsusb" and it should appear in the list. 

Note : write only what is between the commas (").

---

### Post by damianos t on 2013-01-12
I will not have access to my ubuntu computer until monday.
Meanwhile, could you write which command should I use in order to check whether the connection to the printer is ok?
The printer is connected to the computer via ethernet LAN cable, so I believe that it is called network printer, even if it is connected only to one computer.
I believe that maybe the problem is not with the drivers of the printer but with the ethernet connection.
Thank you for the support so far!

---

### Post by damianos t on 2013-01-14
#ii  hplip                                     3.12.6-3ubuntu4                           i386         HP Linux Printing and Imaging System (HPLIP)
ii  hplip-data                                3.12.6-3ubuntu4                           all          HP Linux Printing and Imaging - data files
ii  hplip-gui                                 3.12.6-3ubuntu4                           all          HP Linux Printing and Imaging - GUI utilities (Qt-based)

That appears when I wrote the command that you told me.

---

### Post by damianos t on 2013-01-14
when I run the hp-setup/device discovery/ network-ehternet, the result is: no devices found

In the software center when I search for hplip, I got:
hplip, hplip fax utility, hptoolbox
all installed.

that is why I thing that maybe the OS cannot see the ethernet cable.
Is there a command that checks the ethernet - network connection with the printer?

---

