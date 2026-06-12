---
title: "Printer driver for MG2520"
date: 2014-06-19
forum: Hardware
---

### Post by tom112 on 2014-06-19
I am having trouble adding new printer (Canon Pixma MG2520) to ubuntu 13.1
Canon tech support does not support Linux/ubuntu OS. The MG3222 was printing fine for weeks and then quit working 6/15/14, so purchased a MG2520.
Can load printer and set defaults but test print does not work. Any ideas to get printer working with ubuntu/Linux?

---

### Post by pdc on 2014-06-20
Can I suggest you use the driver that Canon supplies for your printer?

Canon supplies linux drivers for its current printers; it supplies them in 32bit and 64bit; and in rpm, debian and source code flavours;

to get a driver, I start here [http://support-asia.canon-asia.com/?personal](http://support-asia.canon-asia.com/?personal)

and drilling down looking for a 2500 series driver in debian format, I get here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100550201.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100550201.html) .....so **_click on this link_** .... and you will download [COLOR="#008080"]cnijfilter-mg2500series-4.00-1-deb.tar.gz[/COLOR]

If you SAVE it and it will end up in your Downloads directory: if you copy and paste the commands below; that are in red; one by one; into a terminal and hit the enter key after each paste ..........

[COLOR="#FF0000"]cd Downloads
tar -zxvf cnijfilter-mg2500series-4.00-1-deb.tar.gz
cd cnijfilter-mg2500series-4.00-1-deb
./install.sh[/COLOR]

........an install script will appear and may ask you if usb or network connection ......

_________________

as you may know, Canon supply ScanGearMP to drive the scanner on your device; let us know if you want guidance on the install of that.........

---

### Post by tom112 on 2014-06-20
PDC... Thank you for your suggestion... I downloaded per your instructions (I think)... and openned the AMD64 ver. to match my sys. and recvd and error...
"The package system is broken... Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f"
The following packages have unmet dependencies:

libncurses5: Depends: libtinfo5 (= 5.9+20130608-1ubuntu1) but 5.9+20140118-1ubuntu1 is installed
libpython2.7: Depends: libpython2.7-stdlib (= 2.7.6-8) but 2.7.5-8ubuntu3.1 is installed
              Depends: libc6 (>= 2.15) but 2.19-0ubuntu6 is installed
              Depends: zlib1g (>= 1:1.2.0) but 1:1.2.8.dfsg-1ubuntu1 is installed
python2.7: Depends: python2.7-minimal (= 2.7.6-8) but 2.7.5-8ubuntu3.1 is installed
           Depends: libpython2.7-stdlib (= 2.7.6-8) but 2.7.5-8ubuntu3.1 is installed
This IJ Printer Driver provides printing functions for Canon Inkjet printers operating under the CUPS (Common UNIX Printing System) environment.

---

### Post by pdc on 2014-06-20
> [COLOR="#EE82EE"]... and openned the AMD64 ver. to match my sys.[/COLOR]

Gosh

..........I can't see that I suggested you do that........the install script is there to do that for you; and it installs a common driver and then a 2500 driver in that order; 

the suggestions were you copied and pasted four commands

1) > [COLOR="#FF0000"]cd Downloads[/COLOR]

2) > [COLOR="#FF0000"]tar -zxvf cnijfilter-mg2500series-4.00-1-deb.tar.gz[/COLOR]

3)  > [COLOR="#FF0000"]cd cnijfilter-mg2500series-4.00-1-deb[/COLOR]

4)  > [COLOR="#FF0000"]./install.sh[/COLOR]

______________________________

all I can suggest is you repeat the above; 

you have ensured you have updates? 
[http://askubuntu.com/questions/222348/what-does-sudo-apt-get-update-do](http://askubuntu.com/questions/222348/what-does-sudo-apt-get-update-do)
[https://help.ubuntu.com/12.04/serverguide/apt-get.html](https://help.ubuntu.com/12.04/serverguide/apt-get.html)

---

### Post by tom112 on 2014-07-05
(Solved)

---

### Post by pdc on 2014-07-05
well done; glad to hear it is all working; Canon supply [COLOR="#0000FF"]ScanGearMP[/COLOR] for the scanner side of things; it installs in the way the printer driver does; and runs from a terminal with > [COLOR="#FF0000"]scangearmp[/COLOR] and thereafter one sets up a launcher to automate

---

