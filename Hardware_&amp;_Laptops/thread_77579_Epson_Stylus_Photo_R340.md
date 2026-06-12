---
title: "Epson Stylus Photo R340"
date: 2005-10-17
forum: Hardware &amp; Laptops
---

### Post by Chris Cromer on 2005-10-17
Does anyone know if the Epson Stylus Photo R340 works in Ubuntu? Or even if it works in linux at all with the R300 driver?

According to linuxprinting.org the R300, R310, and R320 work using the R300 driver... but before I buy the R340 I want to know if it will work with the R300 driver or not. Unfortunately linuxprinting.org doesn't mention the R340 at all so I am at a loss and thought I would ask here.

If not, then I guess I need to find another printer.

---

### Post by Chris Cromer on 2005-10-24
I hate doing this... but bump.

---

### Post by emperor on 2005-12-10
[quote=Chris Cromer]Does anyone know if the Epson Stylus Photo R340 works in Ubuntu? Or even if it works in linux at all with the R300 driver?

According to linuxprinting.org the R300, R310, and R320 work using the R300 driver... but before I buy the R340 I want to know if it will work with the R300 driver or not. Unfortunately linuxprinting.org doesn't mention the R340 at all so I am at a loss and thought I would ask here.

If not, then I guess I need to find another printer.[/quote]

Even Epson does not have a linux driver for the R340, they do have R300, R310 and R320 drivers here: tp://www.avasys.jp/english/linux_e/dl_ink.html

I just bought a reburbished R300 at Outpost.com for $49.00 ($69 - $20 rebate). Delivered product was brand new with all 6 sealed ink cart. It was detected in Ubuntu Breezy perfectly; took all of 2 minutes to setup. Front media readers automount and work too! Can import photos directly into Fspot.

      1 4198893     EPSON R300 REFURBISHED $69.99

---

### Post by emperor on 2005-12-15
Update: The native epson drivers from the japanese site ([http://www.avasys.jp/english/linux_e/dl_ink.html](http://www.avasys.jp/english/linux_e/dl_ink.html))
do not seem to work on Ubuntu or FC2. They won't compile from source either do to an error in a non-free binary.

However, the gimp-print drivers in Ubuntu work fine, so far, with the R300.

---

### Post by Chris Cromer on 2005-12-28
Thanks... but I wanted teh R340 since I get an employee discount on it. Well hopefully one day it will work.

---

### Post by deadgobby on 2005-12-29
You are not the first on the that haven this problem. Breezy has bug that is going to be fixed with Drapper. I do not know if you want to wait till April 2006 to get the printer working. Breezy seems to missing supported drivers for printers, scanners, and other stuff. 
 I believe in K.I.S.S. Keep It simple stupid. Please make sure your printer is on when you boot up your system. Let the program locate your printer. Go to System tab and go to printer tab. Once that window is open  go to add printer. See if it will locate your printer. If not going.....
 There is several options here. One option is going to
[http://www.avasys.jp/english/linux_e/dl_ink.html](http://www.avasys.jp/english/linux_e/dl_ink.html)
and Dl the source cup. One option is to Dl the RPM and the other is to Dl the tar ball. I do not know how much you know about Linux or Ubuntu. I hate to assume to your know how on Linux. You can Dl the RPM file. That is fine and some times it is easy to convert that RPM pack and convert it over to Debian package and unpack it. Than Dl the tar file, extract, and install it. So we'll go with both. When you DL the files, save it to desk top. Once you have them on your desktop... Assuming you Dl to desktop. You want to open your Terminal.
We are now going to make the RPM file into a Debian Package.
 At the terminal type in "cd Desktop". In Linux caps are important. Please type in dir or ls. The ls (LS)(lower caps) command will high light will give the files you Dl in red type.
Please type in the following command or copy and paste it to your terminal window
 sudo alien pips-sc65_66s-cups-2.6.2-2.i386.rpm
It will ask for your password and then the system will convert the RPM to a Debian package. Before the next step make sure your Synaptic is closed. If it not close the system will tell you a appliction is all ready open.
Now type ls  (LS)(lower caps) you now made a debain package. Herrrr raaaa!
Now we are ready to depackage this sucker.
 Please type in or copy and past the following comand in your terminal.
sudo dpkg -i pips-sc65-66s-cups_2.6.2-3_i386.deb
The system will now unpack the debian file. How freaken cool. After the depack  please close out the terminal window. "Poof.... gone"
Now we'll go back to our friend Synaptic. Click on the search button . Type in Epson. Wa la de da. you'll see a file called escputil. It should be the secound file down. Click on the square and mark for install. Mark it and click on the apply button .  You can try out your printer, if it not working. Reboot with your printer on and try to print. If no go. Please goto add printer menu and see if the system see's the printer. If not. We'll have to go with a different plan of action.

---

### Post by emperor on 2006-01-01
In my testing, the Epson R3x0 drivers from  here do not work on Ubuntu 5.10 or FC2:  [http://www.avasys.jp/english/linux_e/dl_ink.html]("http://www.avasys.jp/english/linux_e/dl_ink.html")

---

### Post by Chris Cromer on 2006-01-02
What about the R220 then? That's another one we carry that I am interested in.

---

### Post by emperor on 2006-01-02
[quote=Chris Cromer]What about the R220 then? That's another one we carry that I am interested in.[/quote]

Ubuntu 5.10 has the gimpprint driver (ver 4.2) for the Stylus Photo R200. 

The R220 and R340 are supported in gimpprint ver 5.x library.

see: [http://cvs.sourceforge.net/viewcvs.py/gimp-print/print/NEWS?rev=1.250](http://cvs.sourceforge.net/viewcvs.py/gimp-print/print/NEWS?rev=1.250)

---

### Post by JLB on 2006-01-10
[QUOTE=Chris Cromer]What about the R220 then? That's another one we carry that I am interested in.[/QUOTE]

With todays dapper update, gutenprint 5.0 rc2 (?), my r220 works. I now have it connected to a print server for all to share. I never had luck with the avasys drivers. I guess that will have to be back-ported to breezy for you to have a working r220. The earlier gutenprint did not work for me.

hth

J-L

---

### Post by emperor on 2006-01-10
[quote=JLB]With todays dapper update, gutenprint 5.0 rc2 (?), my r220 works. I now have it connected to a print server for all to share. I never had luck with the avasys drivers. I guess that will have to be back-ported to breezy for you to have a working r220. The earlier gutenprint did not work for me.

hth

J-L[/quote]

The R340 will most likely work as well in Drapper now!

---

