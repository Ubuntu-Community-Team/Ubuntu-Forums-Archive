---
title: "Epson Stylus DX4050/4000 scanner"
date: 2006-11-20
forum: Hardware &amp; Laptops
---

### Post by Ole32 on 2006-11-20
Can anybody help me, how to use scanner included in printer Epson Stylus DX4050 (it is the same as DX4000). I tried follow instructions at [https://launchpad.net/distros/ubuntu/+ticket/2479](https://launchpad.net/distros/ubuntu/+ticket/2479) but it doesnt work.
 
scanimage -L shows only my TV card

```
lsusb
Bus 003 Device 003: ID 4146:d2b5 USBest Technology
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 04b8:082f Seiko Epson Corp.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 046d:c00e Logitech, Inc. M-BJ69 Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000
```

Would you be kind enough to send me some instructions how to setup Ubuntu to be able to use this scanner. Thank you

---

### Post by alpage2 on 2006-11-21
Same problem here with my DX4050, and also unable to get the printer working - do I need to find a PPD file for it? And where?

(Running Edubuntu 6.10)

Thanks
Alan

---

### Post by JC_Starter on 2007-01-03
How to install Epson Stylus DX4050 on Xubuntu 6.1

All the commands have to be given with printer 'On' (green led on top has to be green, not flashing).  Printer must also be properly connected on usb-port to your computer.  

Open XFCE Menu => Preferences => Printing 

Click on 'New Printer' and provide a printer name (required).  You may also complete description and location, but this is optional.  
Press 'Forward' button.  In the list under 'Select connection', the Epson Stylus DX4000 must appear.  Select it and press 'forward' button.  On the next screen, select 'Epson' and look for the Stylus DX3850 model, by scrolling down on the list.  Press 'forward' button and confirm by the 'apply' button.  

The screens will close and the printer will be listed under 'Local Printer' by the name you have provided.  You might need to restart to get it working properly.  

Second step: get the scanner working.  From Synaptec packet manager, you must have Xsane installed.  You might also consider installing : libsane, libsane-extras, sane-utils, xsane and xsane-commons.  

Then, open up your favorite terminal-session and list all your usb ports : 

# lsusb

Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 04b8:082f Seiko Epson Corp. 
Bus 002 Device 002: ID 0000:0000  
Bus 001 Device 003: ID 046d:c001 Logitech, Inc. N48/M-BB48 [FirstMouse Plus]
Bus 001 Device 001: ID 0000:0000  

Copy or write down the numbers next to the 'Seiko Epson Corp', here 04b8:082f

Next open the file /etc/sane.d/epson.conf with your favorite text-editor (gvim, gedit, leafpad, ...)

#sudo leafpad /etc/sane.d/epson.conf

Look for the line 

# usb 0x? 0x?

Delete the '#' sign and replace the ? by the numbers you wrote down : 

usb 0x4b8 0x82f

Next, delete the '#' signs in front of the lines : 

usb /dev/usbscanner0
usb /dev/usb/scanner0

Save and exit the editor.  

Open XSane (either by the command line or by the menu) 

Then, type at the command line 

# lsusb 

And remember the bus id and device id from your printer : 

Bus 002 Device 001: ID 04b8:082f Seiko Epson Corp.

Next, in order to avoid right conflicts, change the root rights on your usb port to which the printer is connected.  Do this by typing

# sudo chmod 0666 /proc/bus/usb/002/001

by replacing the bus id and device id with the ones on your system.  

Start Xsane and this must be it.  If you get a permission error while creating the file,  resolve this by : 

# sudo chmod 0666 ~/.sane/xsane/*

Finally, to manage your print-jobs, it can be done from :

[http://localhost:631/admin/](http://localhost:631/admin/)

This must be 'bout it.  It worked on my system, Xubuntu 6.1 with the Xfce desktop.  I hope I have it all, because this is a traduction from a French how-to and my mother tongue and desktop environment is Dutch, so I faced some minor (*ahum*) problems.  Special thanks go to Cedynamix! Hail Cedynamix ! 

[http://www.cedynamix.fr/dotclear/index.php/?2006/10/07/6-installer-une-epson-stylus-color-dx4050-sous-ubuntu](http://www.cedynamix.fr/dotclear/index.php/?2006/10/07/6-installer-une-epson-stylus-color-dx4050-sous-ubuntu)


Cheers

---

### Post by andy_1977 on 2007-02-11
hi i have got a problem with my dx4050,
just brought some copy ink for it but the printer light will not go off which means i cannot print.

DOES ANYONE KNOW HOW I CAN GET AROUND THIS????

---

### Post by timski on 2007-05-02
Trying to install the scanner on the Stylus DX4000, under Ubuntu 7.04. I've followed the method above (except the sudo chmod 0666 ~/.sane/xsane/* part, since that directory doesn't exist). I've also tried the [iscan driver](http://www.avasys.jp/english/linux_e/dl_spc.html).

Currently:
[list][*]lsusb finds the scanner
[*]sane-find-scanner finds the scanner[/list]
But... None of the actual scanning applications I've tried can find the scanner - scanimage -L, xsane, iscan - all fail with words to the effect of no device or unable to send command to scanner.

Any pointers on what I might be missing?

Update: sudo scanimage -L and sudo xsane DO work. So now I'm looking for a solution that doesn't involve sudo gimp (i.e. I want to be able to access the scanner directly from applications, which means no part of the process must require root access).

---

### Post by guitarchris on 2007-06-20
I've am having similar problems to many people with my 3850. A careful read of the sane info reveals that sane requires libusb 1.0-6 whereas Ubuntustudio only has v1.0-4. I reloaded synaptic but it did not mark libusb for upgrade. What do I do next - download the latest version manually I guess. 
If I get it working I'll post a follow-up.

---

### Post by allartk on 2007-07-07
On feisty Fawn you just need to edit /etc/udev/rules.d/45-libsane.rules


So:
```

#sudo gedit /etc/udev/rules.d/45-libsane.rules

```
add this lines 
```

# Epson Stylus DX4050
SYSFS {idVendor}=="04b8", SYSFS{idProduct}=="082f", MODE="664", 
GROUP= "scanner" 

```
near the bottom of the file above LABEL="libsane_rules_end" and save it:

after this just reboot or 
```

# sudo /etc/init.d/udev restart

```
thanks to the already mentioned french people :)

---

### Post by m10 on 2007-09-13
i've got a non working dx4050 it recognises it as it but at the driver selection it marks the dx4200 and there isn't any dx4000 driver. when i try installing with the dx4200 driver and i try printing the printer will split one blank page after the other ..

edit: i didn't even try to scan..

---

### Post by stoodleysnow on 2007-09-23
Help!
Can't get xsane to use my dx4000, have tried the above, but xsane just either picks up the tv card or nothing at all. Printing works OK, but I need it to scan!

---

### Post by stoodleysnow on 2007-09-24
BUMP.:guitar:

---

### Post by stoodleysnow on 2007-09-27
bump....
:(

---

### Post by stoodleysnow on 2007-10-02
Problem solved.

(EDIT)
Through synaptic install libsane, libsane-extras and xsane
then
follow JC_stater's instructions (except the chmod of a usb file that doesn't exist) on post 3
then follow allartk's instructions on post 7.

WORKS WITH 7.04 and 7.10
Epson Stylus DX4000 and DX4050

SOLVED:guitar:

---

### Post by smauleon on 2007-10-12
Well, I followed JC_starter's instructions (except referring to ...sane/xsane permissions) and those from allartk. I also have the libsane, libsane-extras and xsane packages installed.

My Epson DX4000 scans now. I can stop switching to Windows when I have to scan. Thank you all!

Just one thing: My epson.conf file had two lines uncommented, referring to a SCSI scanner, and another one saying simply "usb". I commented out them all. I can't say whether this was useful.

smauleon

---

### Post by m10 on 2007-10-19
what do you mean with "JC_starter's instructions"?

---

### Post by stoodleysnow on 2007-10-19
> **m10 said:**
> what do you mean with "JC_starter's instructions"?

I think that's a reference to post 3 in this thread.:)
I've now updated my solution post to include everything I did to make it work.
Hope it's good.

---

### Post by bshephard on 2007-10-21
After much faff trying to get my scanner working in gutsy I've finaly managed to get it working
as a user so i don't have to be root or set permissions at each boot / plug in scanner


Getting an epson stylus dx4000 scanner working under ubuntu gutsy
when working scanner is picked up as cx4000 but works fine

open a terminal

$sudo gedit /etc/sane.d/epson.conf

add following line at end of file and save

usb 0x04b8 0x082f


after this point scanner should work but only as root
to change permissions users are by default added to the group called "scanner"
could be worth a chek first use GUI 

system>admin>users and groups
click manage groups
look for scanner select and click properties
you should see a tick next to your name if not tick it
click ok and close group and user settings

In the terminal again type this
$sudo gedit /etc/udev/rules.d/45-libsane.rules

Add the epson bit directly under the last dell one but before the label bit so the end of the file looks like this
then save and exit

# Dell 1600n
SYSFS{idVendor}=="413c", SYSFS{idProduct}=="5250", MODE="664", GROUP="scanner"
# Epson Stylus DX4050
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="082f", MODE="664", GROUP="scanner"

LABEL="libsane_rules_end"


in the terminal run the following command to re load everything 

sudo /etc/init.d/udev restart

scanner should now work as an ordinary user

open xsane from the menu and if prompted choose your scanner the cx4000 (not the tv card or webcam)

if your still stuck you can get me on aol screen name binky bollwievel

apologies for my grasp of english but i am from nottingham so there

---

### Post by marklid on 2007-10-30
> **stoodleysnow said:**
> Problem solved.

(EDIT)
Through synaptic install libsane, libsane-extras and xsane
then
follow JC_stater's instructions (except the chmod of a usb file that doesn't exist) on post 3
then follow allartk's instructions on post 7.

WORKS WITH 7.04 and 7.10
Epson Stylus DX4000 and DX4050

SOLVED:guitar:

Thanks all, worked a treat on 7.10 :guitar:

---

### Post by barryp3uk on 2007-12-05
Hi everyone

I run Ubuntu but my problem was in PCLOS. I thought I'd post the solution here anyway in case it came in useful.

I was able to follow these instructions & they were very helpful but I still had no joy.

Then I read the Sane page

here:

[http://tldp.org/HOWTO/Scanner-HOWTO/troubleshooting.html](http://tldp.org/HOWTO/Scanner-HOWTO/troubleshooting.html)

& I took a look at this file


/etc/sane.d/dll.conf

It contains a long list of names. Guess what? For some reason Epson was commented out! Hooray, all works now.

---

### Post by maiteeee on 2008-05-28
Hi,
My scanner did work properly but now all it scans is black and white..
Does anyone know where to change settings, because I didn't touch anything and scanned things where in color yesterday:confused:

please help me.

---

