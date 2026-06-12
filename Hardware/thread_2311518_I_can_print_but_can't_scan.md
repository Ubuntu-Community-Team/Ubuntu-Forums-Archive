---
title: "I can print but can't scan"
date: 2016-01-27
forum: Hardware
---

### Post by albaqui on 2016-01-27
Hi

My printer/scanner is Brother MFC 240 C. I was directed to download brscan2....64amd. I tried to install as per brother's website advice. But not installed. it says permission denied. Anyway can anybody help me please from the beginning, and in easy way. Thanks.

---

### Post by dcsoldschool53 on 2016-01-28
I just did a search for your MFC 240C on Brother's website, and I did not see anything about brscan 64amd. What I did find, was a place that you could download some .deb file for the printer and scanner. Follow the steps to select your OS family. Then, your OS version and click search. It will find the download page for you. Here is the link:
[URL="http://support.brother.com/g/b/downloadtop.aspx?c=us_ot&lang=en&prod=mfc240c_all"]http://support.brother.com/g/b/downloadtop.aspx?c=us_ot&lang=en&prod=mfc240c_all 

[/URL]I hope this will help you.

---

### Post by Bucky Ball on 2016-01-28
*Thread moved to **Hardware**.*

---

### Post by albaqui on 2016-01-28
I went to this link. I found that required scan driver is in the computer ad I checked by synaptic device manager. But when I try to use simple scan it says no scanner detected.

---

### Post by Bucky Ball on 2016-01-28
Have you gone to 'Printers' and 'Add Printer' then selected the driver when you get to it during that process?

---

### Post by dcsoldschool53 on 2016-01-28
Turn on your printer, and then, click on simple scan. In simple-scan, click "Document". Click Preferences. When Preferences opens, look for Scan Source, and click the down arrow next to it to see if your printer is listed there. Now select your printer.

---

### Post by albaqui on 2016-01-28
I followed ur instructions but when I click simple scan it shows cannot connect. Next to simple scan is  one page, All page, text, photo. No document or preference. Thanks

---

### Post by albaqui on 2016-01-28
i also tried to scan by GSCAN2PDF.
i downloaded and installed by using ubuntu software center, without terminal. It shows installed, like simple scan. When i click the icon, it says no scanner device detected. I think somehow, my both scanner softwares can not detect MFC-240 C scanner

---

### Post by dcsoldschool53 on 2016-01-28
Here is a picture of simple-scan
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=267004&d=1454017064[/IMG]

Do you see it on your copy of simple scan on your computer? If you do, click Document

---

### Post by dcsoldschool53 on 2016-01-28
If you don't see it, we have two different copies of the program.

---

### Post by albaqui on 2016-01-28
thank you for helping.
here i don't see Document  Page  Help
but rest all are coming

---

### Post by albaqui on 2016-01-28
no, i cant see  Document  Page  Help
but lower all are there

---

### Post by albaqui on 2016-01-28
please send suitable program for me

---

### Post by Bucky Ball on 2016-01-28
Simple Scan is a suitable program. If two apps are not seeing your device I doubt it has anything to do with the software. More like the drivers are not correctly installed for the device, the printer hasn't been installed correctly in Ubuntu, or you have a dead connection (if you are trying to do this wirelessly then the printers wireless is off, if via USB, the cable may be dead). 

Let's go back a step. Does the printer print? Not scan, but can you print a document? Go to a web browser and in the address bar type 'localhost:631' and hit return. You will see the cups interface. Look for your printer there. Is it installed? Can you find it under the printers you have installed? If so, what driver is it showing? The correct one?

---

### Post by plucky on 2016-01-29
With printer connected and powered on,post output from a terminal for ```
lsusb
dpkg -l | grep Brother
``` will show us if printer is connected and what drivers are installed.

Good Luck

---

### Post by davidvandoren on 2016-01-29
Read this and follow the instructions. 

[http://ubuntuforums.org/showthread.php?t=1594558&p=11578647#post11578647](http://ubuntuforums.org/showthread.php?t=1594558&p=11578647#post11578647)
especially 
this. > [COLOR=#000000]Code:[/COLOR][COLOR=#000000]# vi /lib/udev/rules.d/40-libsane.rules[/COLOR]
[COLOR=#000000](at end of libsane_matched rules, add line)[/COLOR]

[COLOR=#000000]Code:
# Brother scanner DCP-350C [/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono]ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="01d0", ENV{libsane_matched}="yes"[/FONT][/COLOR]

You'll have to restart the session or pc after that, to make it work. 


Better try this install script from Brother first.
[http://support.brother.com/g/b/downloadend.aspx?c=us_ot&lang=en&prod=mfc240c_all&os=128&dlid=dlf006893_000&flang=4&type3=625](http://support.brother.com/g/b/downloadend.aspx?c=us_ot&lang=en&prod=mfc240c_all&os=128&dlid=dlf006893_000&flang=4&type3=625)

---

### Post by albaqui on 2016-01-29
I typed local host:631 and clicked, the following appeared,

[TABLE="class: indent, width: 1063"]
[TR]
[TD][h=1]CUPS 1.5.3[/h]CUPS is the standards-based, open source printing system developed by [Apple Inc.]("http://www.apple.com/") for Mac OS[SUP]®[/SUP] X and other UNIX[SUP]®[/SUP]-like operating systems.
[/TD]
[TD][[IMG]http://localhost:631/images/cups-icon.png[/IMG]]("http://www.cups.org/")[/TD]
[/TR]
[/TABLE]
[TABLE="class: indent, width: 1063"]
[TR]
[TD][h=2]CUPS for Users[/h][Overview of CUPS]("http://localhost:631/help/overview.html")
[Command-Line Printing and Options]("http://localhost:631/help/options.html")
[What's New in CUPS 1.5]("http://localhost:631/help/whatsnew.html")
[User Forum]("http://www.cups.org/newsgroups.php?gcups.general")
[/TD]
[TD][h=2]CUPS for Administrators[/h][Adding Printers and Classes]("http://localhost:631/admin")
[Managing Operation Policies]("http://localhost:631/help/policies.html")
[Printer Accounting Basics]("http://localhost:631/help/accounting.html")
[Server Security]("http://localhost:631/help/security.html")
[Using Kerberos Authentication]("http://localhost:631/help/kerberos.html")
[Using Network Printers]("http://localhost:631/help/network.html")
[cupsd.conf Reference]("http://localhost:631/help/ref-cupsd-conf.html")
[Find Printer Drivers]("http://www.cups.org/ppd.php")
[/TD]
[TD][h=2]CUPS for Developers[/h][Introduction to CUPS Programming]("http://localhost:631/help/api-overview.html")
[CUPS API]("http://localhost:631/help/api-cups.html")
[Filter and Backend Programming]("http://localhost:631/help/api-filter.html")
[HTTP and IPP APIs]("http://localhost:631/help/api-httpipp.html")
[PPD API]("http://localhost:631/help/api-ppd.html")
[Raster API]("http://localhost:631/help/api-raster.html")
[PPD Compiler Driver Information File Reference]("http://localhost:631/help/ref-ppdcfile.html")
[Developer Forum]("http://www.cups.org/newsgroups.php?gcups.development")
[/TD]
[/TR]
[/TABLE]


Then i clicked "Find Printer Drivers" and it showed the following,
[h=1]Not Found[/h][COLOR=#000000][FONT=Times New Roman]The requested URL /ppd.php was not found on this server.

Thanks.[/FONT][/COLOR]
[HR][/HR]Apache/2.2 Server at [www.cups.org](www.cups.org) Port 80

---

### Post by albaqui on 2016-01-29
thanks for reply.
I typed as above but little confused
like what is tall line after dpkg -l  ? grep Brother
I don't find in my computer.

---

### Post by albaqui on 2016-01-29
Thanks

I FOUND MY PRINTER'S NAME 
STATUS SHOWS IDLE

---

### Post by plucky on 2016-01-29
> **albaqui said:**
> thanks for reply.
I typed as above but little confused
like what is tall line after dpkg -l  ? grep Brother
I don't find in my computer.

The character | is called the vertical bar/pipe on my keyboard is next to the left shift key above the \ symbol.

Try copy and paste the command into a terminal window.

```
dpkg -l | grep Brother
```

Good Luck

---

### Post by Bill Roberts on 2016-01-30
The missing link here is the brsaneconfig# program. There currently 4 versions.  If the Brother driver install worked correctly, the right one will be present. When I downloaded the installation for my Brother MFC-9349CDW, the brsaneconfig4 program was installed. When I run brsaneconfig4 -h I get the help. 
USAGE: brsaneconfig4 [-OPTION]   OPTION:
       -a name=FRIENDLY-NAME model=MODEL-NAME ip=xx.xx.xx.xx    
       -a name=FRIENDLY-NAME model=MODEL-NAME nodename=BRN_xxxxx 
                   : Add network scanner
       -r FRIENDLY-NAME [FRIENDLY-NAME ...]
                   : Remove network scanner
       -q          : Query supported models and available network scanners
       -d          : Diagnosis
       -p          : Ping (for network scanners)  
       -s:[LABEL]  : Save current configuration
       -l:[LABEL]  : Load saved configuration

Use -q to determine the current setup. If your scanner isn't there, use -a to add it. If it's a network printer you will need the ip address.

---

