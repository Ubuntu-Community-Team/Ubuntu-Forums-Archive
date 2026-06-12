---
title: "LBL 3300 Printer Driver"
date: 2010-02-12
forum: Hardware
---

### Post by Murali krishna on 2010-02-12
I have installed UBUNTU 9.10, when i tried to install CANON LBP 3300 printer i am unable to get the printer drivers. I have searched on the forums and found some links regarding this.

They askked me to download some .tar file and install it, i have tried so...

The printer is installed but when i tried to get the printouts the job status it is showing as print is under processing.\

I have waited for long time, but unable to get the prints...


can Anybody suggest the process to install the Printer of CANON LBP 3300 and get the prints.

---

### Post by depaulmathew on 2010-03-29
I got the same problem.

---

### Post by mihai1984 on 2012-10-28
Hell yeah. 
I have the drivers. Everything is ok except it won't print.
The jobs are sent to the printer, processed then nothing happens.
I am using Ununte 12.04 TLS 64BIT version.
I want to uninstall sorry. I have tried everthing on the internet.
Nothing works.

---

### Post by offgridguy on 2012-10-28
I am not familiar with canon printers, but if indeed they are incompatible with
ubuntu you can post that here and help everyone,

**** 			                          			 			[Desktop Hardware Incompatibility List.]("http://ubuntuforums.org/showthread.php?t=361237&highlight=canon+printer")

Before you do that though perhaps you could search the threads under
canon printer,   if you haven't already.  :)

---

### Post by pdc on 2012-10-28
you sound very fed up .........

you say LBL .............but you mean LBP ........??


can we check the drivers are installed fine .......

can you **[COLOR="Magenta"]copy and paste[/COLOR]** this command

> [COLOR="Red"]sudo dpkg -l | grep Canon[/COLOR]

 .......and **[COLOR="Magenta"]copy and paste[/COLOR]** the results back ............

and also what do you get with 

> [COLOR="Red"]captstatusui -P LBP3300[/COLOR]


_________________________________________________________________

If the drivers are installed, the next steps should be:

[COLOR="SeaGreen"]**2. Register the printer**[/COLOR]

> [COLOR="Red"]sudo /usr/sbin/lpadmin -p LBP2900 -m CNCUPSLBP3300CAPTK.ppd -v ccp://localhost:59787 -E[/COLOR]


............................in Ubuntu 12.04 it is said ........"Ubuntu 12.04 has again blacklisted the usblp module"..........I didn't find this to be so with Mint, so my printer works by ignoring this ubuntu-specific advice...........



In post #4 of this thread

[http://ubuntuforums.org/showthread.php?t=1982917](http://ubuntuforums.org/showthread.php?t=1982917)

Sivella, who is very good on the LBP continues the story that I have described above:

3) **[COLOR="SeaGreen"]Register the printer with ccpd daemon:[/COLOR]**

> [COLOR="Red"]sudo /usr/sbin/ccpdadmin -p LBP3300 -o /dev/usb/lp0[/COLOR]



4) [COLOR="SeaGreen"][B]Start ccpd daemon:
[/B][/COLOR]

> [COLOR="Red"]sudo /etc/init.d/ccpd start[/COLOR]


**[COLOR="SeaGreen"]5. Test the install:[/COLOR]**

> [COLOR="Red"]captstatusui -P LBP3300[/COLOR]


will open the Statusmonitor window. If the message "Ready to print" is displayed --> all is OK.

**_[U]*[COLOR="SeaGreen"]Try to print something.[/COLOR]*_[/U]**

---

