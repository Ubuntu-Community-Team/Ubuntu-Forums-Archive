---
title: "Problem getting brother dcp-110c printer to work"
date: 2012-09-25
forum: Hardware
---

### Post by Klasanov on 2012-09-25
I've been fussing with this for awhile now. I downloaded the 32 bit drivers for the brother dcp-110c printer off of the website and installed them using dpkg. But I can't print to anything in libreoffice. all that shows up is "generic printer"

I looked in cups, and under add printers it has other stuff, but not brother. I've also checked to make sure the drivers were installed via command line.

lsusb gave me 

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b070 Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 002 Device 003: ID 054c:0243 Sony Corp. MicroVault Flash Drive
Bus 005 Device 002: ID 046d:c045 Logitech, Inc. Optical Mouse


and lpstat -v gave me 
lpstat: No destinations added.

i don't have lpd installed.

I tried downloading the 64 bit version after the 32 bit version but that installation failed due to i think the 32 bit driver being installed.

Any ideas?

---

### Post by Klasanov on 2012-09-25
oh and i'm using ubuntu 12.04 i'm pretty sure

---

### Post by pdc on 2012-09-25
[COLOR="Red"]1)[/COLOR] can you tell us what

> sudo dpkg -l | grep Brother

gives in a terminal, by copying and pasting the above command

( vertical line is a pipe command, created by Shift\   )

_________________________________________________________________-

[COLOR="Red"]2)[/COLOR] if you paste this into a spare browser window, 

[http://localhost:631/printers/](http://localhost:631/printers/)

........do you see any mention of your printer.......this page looks inside your system at the printer setup..........................

___________________________________________________________________

[COLOR="Red"]3)[/COLOR] I note your printer is not appearing on lsusb ........

.........it is plugged in and turned on.....?

.....is it connected through an intermediary hub....

.....some folks suggest ensuring it is directly plugged into a usb port on  your computer; that you know works........

........if it were being read by lsusb, I suspect its ID would be

> ID **[COLOR="SeaGreen"]04f9:0169[/COLOR]** Brother Industries, Ltd 

......if you subscribe to the thread: top right: thread tools, subscribe

---

### Post by Klasanov on 2012-09-26
sudo dpkg -l | grep Brother gives me 

ii  brother-cups-wrapper-common              1.0.0-10-0ubuntu5                          Common files for Brother cups wrapper packages
ii  brscan:i386                              0.2.4                                      Brother CUPS Printer Definitions
ii  brscan-skey:i386                         0.2.3-0                                    Brother Linux scanner S-KEY tool
ii  printer-driver-ptouch                    1.3-3ubuntu0.1                             printer driver Brother P-touch label printers

going to [http://localhost:631/printers/](http://localhost:631/printers/) says
"no printers"

I have it plugged in, and turned on
lsusb doesn't give me anything like that
its output is 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b070 Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 002 Device 003: ID 054c:0243 Sony Corp. MicroVault Flash Drive
Bus 005 Device 004: ID 046d:c045 Logitech, Inc. Optical Mouse

---

### Post by Merrattic on 2012-09-26
So are you running 32 bit or 64 bit Ubuntu? If 64 bit uninstall the 32 bit drivers and try the 64 bit ones?

The drivers are in the repos, so use those and install with synaptic/software centre, you only need to go to the brother site for the scanner driver and scanner key tool.

Also, you should be getting something back from lsusb ? Check connections, try different cable etc.

---

### Post by Klasanov on 2012-09-26
Uninstalled the 32 bit drivers and installed the 64 bit ones from Brother, but I'm unsure as to which drivers I need from synaptic. When I type in dcp-110c I get two things. One is brther-lpr-drivers-extra, and the other brother-cups-wrapper-extra is  and installing them doesn't seem to do anything.

---

### Post by pdc on 2012-09-27
lsusb surely has to [COLOR="Red"]SEE[/COLOR] your printer;

eg when I turn my printers on I get

Bus 001 Device 007: ID 04a9:1752 Canon, Inc.

and 

Bus 001 Device 008: ID 04a9:26db Canon, Inc.

---

### Post by Klasanov on 2012-09-28
Well the computer recognizes the printer now. cable wasn't plugged in all the way into the printer.

But now, when I print something, it cancels it before doing anything. Automatically.

Any ideas?

---

### Post by pdc on 2012-09-28
> cable wasn't plugged in all the way into the printer

.......good work to fix that.

____________________________________________________

1) now copy and paste this command

> sudo dpkg -l | grep Brother

.......and copy and paste back what you get

____________________________________________________

2) paste this into a spare browser window

[http://localhost:631/printers/](http://localhost:631/printers/)

and see if the printer is loaded there; this is the CUPS page

_____________________________________________________

3) report back

---

### Post by Klasanov on 2012-09-28
sudo spkg-l | grep Brother tells me

ii  brother-cups-wrapper-common              1.0.0-10-0ubuntu5                          Common files for Brother cups wrapper packages
ii  brscan                                   0.2.4                                      Brother CUPS Printer Definitions
ii  brscan-skey                              0.2.3-0                                    Brother Linux scanner S-KEY tool
ii  printer-driver-ptouch                    1.3-3ubuntu0.1                             printer driver Brother P-touch label printers





[http://localhost:631/printers/](http://localhost:631/printers/) tells me

dcp-110c    dcp-110c  generic text-only printer     idle

---

### Post by pdc on 2012-09-29
I just wonder if you have installed the two drivers needed:

you report:

 > ii brother-cups-wrapper-common 1.0.0-10-0ubuntu5 Common files for Brother cups wrapper packages

in contrast see my thumbnail canon.png where my system shows 2 drivers; I don't know brother but would expect the lpr to be reported too..

I enclose a thumbnail lpr.png showing the two drivers Brother expects you to install: in the order of *[COLOR="Red"]lpr first[/COLOR]* and then [COLOR="Red"]*cups-wrapper second*[/COLOR]

________________________________________________________________

your cups report of 

> dcp-110c dcp-110c generic text-only printer idle 

......sounds deficient..........

see my thumbnail cups.png to see what mine looks like

______________________________________________________________

so...........*[COLOR="Red"]I'm speculating now[/COLOR]* you don't have the lpr driver installed;

........if that were so, it would be best to delete the cups-wrapper;

and start again: install lpr first and then cupswrapper, as instructed here

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html)

---

### Post by kurt18947 on 2012-09-29
I've had quite good luck using Brother's installer script.  I'd probably uninstall everything possible then run the installer in a terminal.

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00104](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00104)

I downloaded the script and posted it as an attachment in post #4 here:

[http://ubuntuforums.org/showthread.php?t=1999216&highlight=brother](http://ubuntuforums.org/showthread.php?t=1999216&highlight=brother)

I didn't find Brother's method of downloading the script particularly intuitive:rolleyes:.  It has worked well on a few installs for me though.  For a network connection I've found a static i.p. on the printer and using the 'socket' protocol to be the most reliable. YMMV though.

---

### Post by Klasanov on 2012-10-06
I had a reply but the forum mjust have eaten it or something.

How do I remove

rc  brscan                                   0.2.4                                      Brother CUPS Printer Definitions
ii  brscan-skey                              0.2.3-0                                    Brother Linux scanner S-KEY tool

from dpkg? I removed stuff from synaptic but these still show up

---

### Post by Klasanov on 2012-10-14
bump

---

### Post by plucky on 2012-10-14
> **Klasanov said:**
> bump

Open Synaptic Package Manager and search for **dcp-110c** and you should find **brother-cups-wrapper-extra** and **brother-lpr-drivers-extra**.

Select both and install.

Then run ```
dpkg -l | grep -i brother
``` and you should see ```
dpkg -l | grep -i brother
ii  brother-cups-wrapper-common           1.0.0-10-0ubuntu5                               Common files for Brother cups wrapper packages
ii  brother-cups-wrapper-extra            1.2.1-0ubuntu3                                  Cups Wrapper drivers for extra brother printers
ii  brother-lpr-drivers-common            1.0.0-4-0ubuntu1                                Common files for brother-lpr-drivers packages
ii  brother-lpr-drivers-extra             1.2.0-2-0ubuntu3                                LPR drivers for extra brother printers
ii  brscan-skey                           0.2.1-3                                         Brother Linux scanner S-KEY tool
ii  brscan2                               0.2.5-1                                         Brother Scanner Driver

```

That means the drivers are installed.

Now connect and power on the printer and you should now be able to select the correct driver for your printer.


Good Luck

---

### Post by Klasanov on 2012-10-17
I installed those. dpkg tells me

ii  brother-cups-wrapper-common              1.0.0-10-0ubuntu5                          Common files for Brother cups wrapper packages
ii  brother-cups-wrapper-extra               1.2.1-0ubuntu3                             Cups Wrapper drivers for extra brother printers
ii  brother-lpr-drivers-common               1.0.0-4-0ubuntu1                           Common files for brother-lpr-drivers packages
ii  brother-lpr-drivers-extra                1.2.0-2-0ubuntu4                           LPR drivers for extra brother printers
rc  brscan                                   0.2.4                                      Brother CUPS Printer Definitions
ii  brscan-skey                              0.2.4-0                                    Brother Linux scanner S-KEY tool
ii  brscan2                                  0.2.5-1                                    Brother Scanner Driver


However, when  I open libreoffice and go to print, it just tells me that I have "generic printer"

---

### Post by plucky on 2012-10-17
After the drivers have been installed,you have to add the printer again.

Try using the CUPS interface.Open Firefox and put in the address bar ```
http://127.0.0.1:631/admin
``` and that will open the CUPS interface.You can then view whether CUPS sees your printer.

Good Luck

---

