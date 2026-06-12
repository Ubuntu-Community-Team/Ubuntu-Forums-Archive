---
title: "Printer/scanner Brother DCP 7045N Printer margins problem"
date: 2010-02-04
forum: Hardware
---

### Post by ghed on 2010-02-04
I have installed my printer Brother DCP 7045N. When the test page and other pages are printed there are left margin and bottom margin so the top right part of the page is not printed. Ubuntu 9.10. Have seen the problem in other furums but no solution.

---

### Post by aymeric on 2010-02-05
Same problem here, Ubuntu 9.10 on several computers in a small local network, same margin problems.

I used the PPD file from Brother.com in "add network printer.

I reported the problem on Ubuntu France boards and no reply at this time...

If anyone has the solution, it would be great !

---

### Post by ghed on 2010-02-05
A simple solution to the problem is to change the driver for the printer using CUPS 1.4.1 to DCP-7025 Foomatic/Postscript.
Go to [http://localhost:631/printers](http://localhost:631/printers) and select your printer (or install from here)
For a network printer, go to Administration > Modify Printer and choose LPD/LPR Host or Printer" or "AppSocket/HP JetDirect
Write your URL lpd://nnn.nnn.nnn.nnn (you will find the adress on the menu of the printer, network ...)
Install the driver for DCP-7025 Foomatic/Postscript an print the test page. It worked for me. Good Luck :D

---

### Post by ghed on 2010-02-19
The problem with the margin came back today. I don't understand why. Was it an update of the CUPS or something. :mad:
I have reinstalled the printer
 
this is installed
 
root@h-desktop:/# dpkg -l | grep Brother
ii brdcp7045nlpr 2.0.2-1 Brother DCP-7045N LPR driver
ii brscan-skey 0.2.1-3 Brother Linux scanner S-KEY tool
ii brscan3 0.2.9-1 Brother Scanner Driver
ii cupswrapperdcp7045n 2.0.2-1 Brother DCP7045N CUPS wrapper driver
 
I have also run the [http://localhost:631/printers/](http://localhost:631/printers/) and followed the instructions on [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html).
 
 
At least I think I have followed the instructions. If I try the PPD file the computer stops completely.
Greatful for help with this.
 
Have also tried 6. Adjust the print margins. in [http://www.linuxfoundation.org/collaborate/workgroups/openprinting/database/cupsdocumentation](http://www.linuxfoundation.org/collaborate/workgroups/openprinting/database/cupsdocumentation) it seems though that is has no effect at all on the print margins
 
News in the matter. 
 
Downloaded the package
[http://www.linuxfoundation.org/collaborate/workgroups/openprinting/database/driverpackages](http://www.linuxfoundation.org/collaborate/workgroups/openprinting/database/driverpackages)
 
For this we plan to index our package repositories so that they can be looked up by yum (Red Hat, Fedora, SUSE, ...), zypper (SUSE), urpmi (Mandriva), apt-get (Debian, Ubuntu, ...).
apt-get
Indexing for apt-get we have already working. Add the line
deb [http://www.openprinting.org/download/printdriver/debian/](http://www.openprinting.org/download/printdriver/debian/) lsb3.2 mainto your /etc/apt/sources.list file and run
sudo apt-get updateFrom now on your package installation tools will also list our packages and if you have installed packages from us, they will be taken into account on the daily automatic updates.
 
Now the printer works :-)

---

### Post by dpardo on 2010-09-22
The solution for me was select the "Brother DCP-8045D - CUPS+Gutenprint v5.2.4" driver at the model list.

---

