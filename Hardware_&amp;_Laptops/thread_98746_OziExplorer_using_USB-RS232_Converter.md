---
title: "OziExplorer using USB-RS232 Converter"
date: 2005-12-04
forum: Hardware &amp; Laptops
---

### Post by cha4591929 on 2005-12-04
Hi All, 

Is there any way i can symlink port ttyUSB0 to ttyS0  ??
I have installed OziExplorer 3.95.4i using wine and i must say almost everything is working very well. I can import maps etc from Raster , however the options avail for the program only allow me to sellect com ports 0 -15 to communicate with my Garmin GPS72..  The laptop i have does not come with a serial port so i have purchased a USB-RS232 converter which by the log below [ # dmesg ] is doing what it is supposed to do.

[4294700.448000] usbcore: registered new driver usbserial_generic
[4294700.448000] drivers/usb/serial/usb-serial.c: USB Serial Driver core v2.0
[4294700.455000] drivers/usb/serial/usb-serial.c: USB Serial support registered for MCT U232
[4294700.458000] mct_u232 4-1:1.0: MCT U232 converter detected
[4294700.463000] usb 4-1: MCT U232 converter now attached to** ttyUSB0**
[4294700.463000] usbcore: registered new driver mct_u232
[4294700.463000] drivers/usb/serial/mct_u232.c: Magic Control Technology USB-RS2 32 converter driver z2.0

I am not sure what options i have available ?? Has anyone had a similar problem that they could shed some light on..

Cheers


Chris

---

### Post by ranf on 2005-12-04
[QUOTE=cha4591929]
Is there any way i can symlink port ttyUSB0 to ttyS0  ??
I have installed OziExplorer 3.95.4i using wine and i must say almost everything is working very well. I can import maps etc from Raster , however the options avail for the program only allow me to sellect com ports 0 -15 to communicate with my Garmin GPS72..  The laptop i have does not come with a serial port so i have purchased a USB-RS232 converter which by the log below [ # dmesg ] is doing what it is supposed to do.
[/QUOTE]
Did you have a look at `gpsdrive' and other Linux programs specifically for Garmin GPS's?
A lot of GPS related stuff can be found here:
[http://gpsinformation.net/](http://gpsinformation.net/)

---

### Post by alhanduin on 2007-11-13
Hey i have the same problem and i have solvedit doing doig what this how to say: (i use oziexplorer but the comunication will need the same procedure):

Running OziExplorer under LINUX
(Contributed by an OziExplorer user)

(Note: We do not have a Linux version of OziExplorer but a user has OziExplorer running using this procedure.)

Linux Distribution: Ubuntu Linux 6.06 LTS "Dapper Drake"
OziExplorer version: 3.95.4m
Wine version: 0.9.16

I succeeded in making OziExplorer work, apparently with all features...

Full Procedure:

Step 1. Install "Wine" (I followed the instructions in the "ubuntu user documentation" to get the latest version):
First, in Synaptic, add the following repository

deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

Then, reload, update, and install wine
When you first run wine, it will create a .wine directory in you home dir. Inside it, will be a "drive_c" that simulates the windows environment.

**If you're using another linux distribution, download the software from [http://www.winehq.com](http://www.winehq.com) and follow the instructions)

Step 2. copy the file "oziexp_setup. exe" to ~/.wine
I tried running it from another location, but it failed (I don't know why)

Step 3. In the terminal, change to the "~/.wine" directory, where oziexp_setup.exe is.

Step 4. Run the OziExplorer installation file with wine. In the terminal, type:

wine oziexp_setup.exe

The setup will install OziExplorer under ~/.wine/drive_c/OziExplorer/
(if you have any trouble here with permissions, try running wine with "sudo". type: "sudo wine oziexp_setup.exe"
If you use another distribution without "sudo" run the command as "root")

The program won't run just yet ...

Thanks to Stephen B, in the "WineHQ" (on Tuesday November 8th 2005) the initial crash problem is solved:
Under ~/.wine/drive_c/OziExplorer/, edit the file "oziexp.ini", adding the following lines (It disables the tooltips at the start):

[Help]
Show Start=0
Getting Started=0

Now it works! (at least it should...)

We just have to setup the gps... Apparently, serial communication works fine, but I can't guarantee it because my GPS connects through USB.
If your GPS connects through serial COM, you must only remember that in linux, COM1=/dev/ttyS0, COM2=/dev/ttyS1, etc.

Step 5. (Additional step required for Garmin USB GPS's)
In the case of USB connection, I use a "Garmin GPS60". Gamin drivers are already built into Ubuntu kernel, so Linux should recognize the device.
After connecting the GPS, run "dmesg" to find out: you should see lines like these:
.....
[17193444.360000] usb 1-3: new full speed USB device using ohci_hcd and address 4
[17193444.560000] garmin_gps 1-3:1.0: Garmin GPS usb/tty converter detected
[17193444.560000] usb 1-3: Garmin GPS usb/tty converter now attached to ttyUSB0
.....

The problem is OziExplorer doesn't recognize "/dev/...", so we can get around the problem making a "sym link" from "COM to USB". I chose COM3 to avoid interference with other things (COM3=/dev/ttyS2).
In the terminal, type:

sudo ln -sb /dev/ttyUSB0 /dev/ttyS2

(the "b" option makes a backup copy of ttyS2 in case you want to "get back")
After that, you must start OziExplorer by typing:

wine ~/.wine/drive_c/OziExplorer/OziExp.exe

In "Ozi", go to the menu "File" > "Configuration" > "GPS" and choose your GPS make and model.
Then, under "COM" choose COM3, leave the "Garmin USB" or other UNCHECKED (this way, the software "thinks" the GPS is under COM3...)
SAVE the configuration and exit.

Step 6. ITS DONE!!! By now, you must be able to communicate to and from the GPS, and have OziExplorer working just fine!

I hope this will help someone...

---

