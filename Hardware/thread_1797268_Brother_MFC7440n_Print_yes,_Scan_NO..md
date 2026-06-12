---
title: "Brother MFC7440n Print yes, Scan NO."
date: 2011-07-04
forum: Hardware
---

### Post by jfbooth on 2011-07-04
This is Xubuntu 11.04.  The 'printer' is a multifunction Brother Printer with scanner.

The Brother worked fine with 10.10. This is a clean install of 11.04.

Here is what I followed using 10.10 with comments in **bold**.  This is a TUTORIAL found at [http://ubuntuforums.org/showthread.php?t=590793](http://ubuntuforums.org/showthread.php?t=590793) :

Scanner:

FIRST MAKE SURE YOUR SYSTEM HAS ALL UPDATES INSTALLED IF YOU HAVE A FRESH INSTALLATION OF UBUNTU.

**DONE**

Step 1:
Locate your model & download the appropriate "Debian" brscan or brscan2 driver from HERE. Please take note that there is a separate driver depending on whether you have a 32bit or 64bit Gutsy installed. Typically it will be 32bit.

**DOWNLOADED brscan3-0.2.11-4.i386.deb FROM BROTHER WEBSITE**

Step 2:

For the brscan3 32bit driver which most will be using Install with the following command in Terminal:

```
sudo dpkg -i brscan3-0.2.11-4.i386.deb
```

**DONE**

Step 3:
Confirm you need to continue on with the following steps, I believe it is only Gutsy that has problems. Simply open Xsane, choose you scanner and click OK. If you get an I/O-Error you will need to continue onto Step 5, if it's all working you're done!

**XSANE HAD TO BE INSTALLED W/ PACKAGE MANAGER.  XSANE GIVES "No Devices Available'**

Step 5:
Give yourself permission to use it! At time of release it's a Gutsy Quirk/Bug... First we need to find out the Vendor ID & Product ID for our scanner or printer/scanner combo.

Type the following in Terminal:

```
lsusb
```

Your output will be something like this:
Code:

```
matthew@matthew-laptop:~/Desktop$ lsusb
Bus 005 Device 004: ID 05ca:1810 Ricoh Co., Ltd 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 03f0:171d Hewlett-Packard 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 062a:0000 Creative Labs Optical Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 003: ID **????:????** Brother Industries, Ltd 
Bus 001 Device 001: ID 0000:0000  
matthew@matthew-laptop:~/Desktop$
```

Locate Brother Industries, Ltd and take note of your Vendor ID Product ID as shown in bold in the above output and adjust Step 6 to match.

**I did not get ANY Brother lines with lsusb**

Step 5:
In Terminal type the following:

_UBUNTU_
```
sudo gedit /etc/udev/rules.d/45-libsane.rules
```

_Kubuntu_
```
sudo kate /etc/udev/rules.d/45-libsane.rules
```

[B]I am using XUBUNTU.  I am a Linux beginner.  Neither of these editors are available.  There is something called MOUSEPAD but it is a GUI application .. don't know what to use in Terminal.  Doesn't matter at this point because 45-libsane.rules does not exist.

From HERE down .. I never got that far.[/B]

At the bottom of the page but before LABEL="libsane_rules_end" add the following changing YOUR-VENOR-ID & YOUR- PRODUCT-ID to yours, both are 4 characters long:

```
# Brother DCP-115C
SYSFS{idVendor}=="YOUR-VENOR-ID", SYSFS{idProduct}=="YOUR-PRODUCT-ID", MODE="664", GROUP="scanner"
```

The last section of 45-libsane.rules should look like this after adding your scanner/printer to the last line:

```

SYSFS{idVendor}=="413c", SYSFS{idProduct}=="5105", MODE="664", GROUP="scanner"
# Dell A960
SYSFS{idVendor}=="413c", SYSFS{idProduct}=="5107", MODE="664", GROUP="scanner"
# Dell 922
SYSFS{idVendor}=="413c", SYSFS{idProduct}=="5109", MODE="664", GROUP="scanner"
# Dell 1600n
SYSFS{idVendor}=="413c", SYSFS{idProduct}=="5250", MODE="664", GROUP="scanner"
# Brother DCP-115C
SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="018c", MODE="664", GROUP="scanner"

LABEL="libsane_rules_end"
```

Step 7:
Save your changes and restart your PC. All going well it will be working!

[B]Like I say .. xsane and simple scan do not detect a scanner though I did restart the machine .. hoping.

Thanks in advance for any help.[/B]

---

### Post by charliewhizbeez on 2011-07-05
Cool.  I also use Xubuntu and a brother MFC (have to hook that up to wireless).  

Just to tell you, mousepad is xubuntu's Kate and gedit. :)

---

### Post by Jose Catre-Vandis on 2011-07-05
For Network setup: Doesn't look like you followed the intialisation requirements for the scanner after you installed the deb.

[B]Setting for your network scanner

***Use brsaneconfig (for brscan models), brsaneconfig2 (for brscan2 models) or brsaneconfig3 (for brscan3 models) accordingly.

5-1. Add network scanner entry

Command  :  

brsaneconfig2  -a  name=(name  your  device)  model=(model  name)  ip=xx.xx.xx.xx


5-2. Confirm network scanner entry

Command  :  

brsaneconfig2  -q  |  grep  (name  of  your  device)[/B]

For USB setup: 

Ubuntu 9.10, 10.04
    1. Open "/lib/udev/rules.d/40-libsane.rules" file.  (create it if it doesn't exist!)
    2.Add the following two lines to the end of the device list. (Before the line "# The following rule will disable ..."):


    The lines to be added--------------------------- 


    # Brother scanners
    ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"
     

    3. Restart the OS.


Check out the Brother driver site:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)

---

### Post by jfbooth on 2011-07-05
> **Jose Catre-Vandis said:**
> For Network setup: Doesn't look like you followed the intialisation requirements for the scanner after you installed the deb.

[B]Setting for your network scanner

***Use brsaneconfig (for brscan models), brsaneconfig2 (for brscan2 models) or brsaneconfig3 (for brscan3 models) accordingly.

5-1. Add network scanner entry

Command  :  

brsaneconfig2  -a  name=(name  your  device)  model=(model  name)  ip=xx.xx.xx.xx


5-2. Confirm network scanner entry

Command  :  

brsaneconfig2  -q  |  grep  (name  of  your  device)[/B]

For USB setup: 

Ubuntu 9.10, 10.04
    1. Open "/lib/udev/rules.d/40-libsane.rules" file.  (create it if it doesn't exist!)
    2.Add the following two lines to the end of the device list. (Before the line "# The following rule will disable ..."):


    The lines to be added--------------------------- 


    # Brother scanners
    ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"
     

    3. Restart the OS.


Check out the Brother driver site:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)

Thank you for your support on this.  From your reply, I gather I need to run brsaneconfig3.  Here are the results:

```
jb@Backroom-Linux:~/Desktop$ brsaneconfig3 -a name=SCANNER model=MFC7440n ip=192.168.001.008
Invalid model name
jb@Backroom-Linux:~/Desktop$
```

I assume 'name' is arbitrary.  I do not know what to provide for model except the model of the Printer/scanner.  Sorry I am such a dunce.

---

### Post by Jose Catre-Vandis on 2011-07-05
Just to check: Are you connecting the printer over the network or via USB ?

Model should be exactly like the model is (as it is written on the printer itself), probably MFC-7440N

---

### Post by jfbooth on 2011-07-05
> **Jose Catre-Vandis said:**
> Just to check: Are you connecting the printer over the network or via USB ?

Model should be exactly like the model is (as it is written on the printer itself), probably MFC-7440N

Network.  Ethernet cable from Printer to Router, Ethernet cable to computer from Router.

You are probably right about the model.  I will try that soon and get back.

THANK YOU for your replies.

---

### Post by Jose Catre-Vandis on 2011-07-05
Right network, in which case you do need to follow the instructions I initially posted that are in bold:
```
sudo brsaneconfig3 -a name=MFC-7440N model=MFC-7440N ip=192.168.1.08


Confirm network scanner entry

brsaneconfig3 -q | grep MFC-7440N
```

Then try a scan with Simple Scan or Xsane

---

### Post by jfbooth on 2011-07-05
> **Jose Catre-Vandis said:**
> [B]Setting for your network scanner

***Use brsaneconfig (for brscan models), brsaneconfig2 (for brscan2 models) or brsaneconfig3 (for brscan3 models) accordingly.

5-1. Add network scanner entry

Command  :  

brsaneconfig2  -a  name=(name  your  device)  model=(model  name)  ip=xx.xx.xx.xx


5-2. Confirm network scanner entry

Command  :  

brsaneconfig2  -q  |  grep  (name  of  your  device)[/B]


I have made a small amount of progress.  Using the correct model name "helped"

```
jb@Backroom-Linux:~$ brsaneconfig3 -a name=SCANNER model=MFC-7440N ip=192.168.001.008
jb@Backroom-Linux:~$ brsaneconfig3 -q | grep MFC-7440N
 91 "MFC-7440N"
  0 SCANNER             "MFC-7440N"         I:192.168.001.008
jb@Backroom-Linux:~$ 
```

NOW, when I run "XSane Image scanning program" from APPLICATIONS/GRAPHICS, a window opens "Scanning for devices" and then closes back to the 'DESKTOP'.  BEFORE, I got a message "No Devices Available'.

Simple Scan OPENS with No error but when try to scan a page, there is animation indicating it is trying and after a long time, an error window opens "Unable to Connect to Scanner".  There is a button to 'change scanner' and when I click on it, it shows:

SCAN SOURCE: BROTHER MFC-7440N

and some other 'logical' settings.

Before ... it also simply gave an immediate 'scanner not found' error.

Now, I am just guessing .. perhaps the problem is (still) the absence of **40-libsane.rules**(?)

In order to create one, I have to get VENDOR ID and PRODUCT ID for this printer which, according to the tutorial, is determined with ```
lsusb
``` except ```
lsusb
``` does not return anything for Brother:

```
jb@Backroom-Linux:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0451:2046 Texas Instruments, Inc. TUSB2046 Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 102 flash drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
jb@Backroom-Linux:~$ 
```

If I knew those two values, I could CREATE the file and maybe it would work.  I think the ```
lsusb
``` routine seems (according to the tutorial) something need to do for GUTZY .. but that is questionable.  

I have a feeling that until I get a valid **40-libsane.rules** file, this isn't going to work .. I need to know the VENDOR/PRODUCT IDs .. but I am also a blind, stumbling noob.

Edit:  Actually, I am not sure I need to edit a 40-libsane.rules file in the first place.  I found an EXAMPLE of a 40-libsane.rules file on the Internet and it clearly says "# To add a USB device, add a rule to the list below between the SUBSYSTEM...
# and LABEL... lines."

This is a NETWORKED printer/scanner.  If I am right, then I totally don't know why it won't scan.  Thing is .. when the same setup ran great on 10.10, I remember lsub giving me the IDs so I COULD edit a 40-libsane.rules file ... I think.  

Truthfully, that tutorial is pretty old .. and so full of replies, it is hard to understand it.  I have it and my memory from when I did it before (and it worked), but with 11.4, I'm not getting what I expect from using the tutorial.

---

### Post by Jose Catre-Vandis on 2011-07-07
Try

```
sudo xsane
```


Also I had similar problem on 10.10. Solved this by locating the Device IDs in a .cfg file located in
```
/usr/local/Brother/sane/
```

The applied the info to the rules as per my post here:

[http://ubuntuforums.org/showpost.php?p=10622869&postcount=372](http://ubuntuforums.org/showpost.php?p=10622869&postcount=372)

---

### Post by jfbooth on 2011-07-07
There seems to be SOME progress.  BEFORE, when I clicked on XSANE (or Simple Scan) from the GUI, all I got was error windows .. no splash screen.

```
sudo xsane
```

this time presented an XSANE splash screen I have never seen before.  To my surprise, it showed TWO scanners.  **Please see attachment**.  I tried scanning with the first one and it **failed to open device 'brother3:net1;dev0'**.  I tried scanning with the second one and it **failed to open device 'brother3:net1;dev1'**.

I assumed I saw this splash screen because of sudo xsane but I tried it AGAIN from GUI and got the same results.

I do not understand what you are conveying in the EDIT part of your reply.

Keep in mind, there is no **45-libsane.rules** file on this machine.  IF I need one, I cannot create one until I find out the Vendor ID and Product Id.  I have been unable to learn that I need one or I don't need one.  It SEEMS one is needed for a USB connection ... which does not apply to me .. so I don't know if that is the problem or not.

I am sure I should NOT have TWO scanners listed as available devices in XSANE.

I want to thank you for your continued support.  Much appreciated.

---

### Post by Jose Catre-Vandis on 2011-07-08
Don't worry about the two scanners, looks like you have simply created two SCANNER and SCANNER1 for the same device. You can edit the config file below to remove one if needs be.

```
sudo nano /usr/local/Brother/sane/brsanenetdevice3.cfg
```
Write down the DEVICE IDS which should look like this:
```
DEVICE=MFC-7440N , "MFC-7440N" , **0x4f9:0x1aa** , IP-ADDRESS=192.168.0.8
```
**NOTE: replace the device IDs I have used here with your own!**

Create a scanner group if one doesn't exist:
```
sudo addgroup scanner
```

Enter this info into your rules file before the last line:
```
sudo nano /lib/udev/rules.d/40-libsane.rules
```

```
# Brother MFC-7440N
SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="01aa", MODE="664", GROUP="scanner"
```


That should be it?

---

### Post by jfbooth on 2011-07-09
> **Jose Catre-Vandis said:**
> Don't worry about the two scanners, looks like you have simply created two SCANNER and SCANNER1 for the same device. You can edit the config file below to remove one if needs be.

```
sudo nano /usr/local/Brother/sane/brsanenetdevice3.cfg
```

OK, I edited it.  It now looks like this:

```
DEVICE=SCANNER , "MFC-7440N" , 0x4f9:0x1e6 , IP-ADDRESS=192.168.001.008
```

> Write down the DEVICE IDS which should look like this:
```
DEVICE=MFC-7440N , "MFC-7440N" , **0x4f9:0x1aa** , IP-ADDRESS=192.168.0.8
```
**NOTE: replace the device IDs I have used here with your own!**

OK .. I wrote down **0x4f9** and **0x1e6**

> Create a scanner group if one doesn't exist:
```
sudo addgroup scanner
```

I have no idea if I have one or not .. so I entered the above code.

> Enter this info into your rules file before the last line:

```
sudo nano /lib/udev/rules.d/40-libsane.rules
```

```
# Brother MFC-7440N
SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="01aa", MODE="664", GROUP="scanner"
```

I FINALLY have a 40-libsane.rules file.  I found one on the INTERNET and edited it.  IF I DID IT RIGHT.  This is what it says:

```
ACTION!="add", GOTO="libsane_rules_end"
ENV{DEVTYPE}=="usb_device", GOTO="libsane_create_usb_dev"
SUBSYSTEMS=="scsi", GOTO="libsane_scsi_rules_begin"
SUBSYSTEM=="usb_device", GOTO="libsane_usb_rules_begin"
SUBSYSTEM!="usb_device", GOTO="libsane_usb_rules_end"

# Kernel >= 2.6.22 jumps here
LABEL="libsane_create_usb_dev"

# For Linux >= 2.6.22 without CONFIG_USB_DEVICE_CLASS=y
# If the following rule does not exist on your system yet, uncomment it
# ENV{DEVTYPE}=="usb_device", MODE="0664", OWNER="root", GROUP="root"

# Kernel < 2.6.22 jumps here
LABEL="libsane_usb_rules_begin"

# Brother MFC-7440N
SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="01e6", MODE="664", GROUP="scanner"

ENV{libsane_matched}=="yes", RUN+="/bin/setfacl -m g:scanner:rw $env{DEVNAME}"

LABEL="libsane_scsi_rules_end"
```

PLEASE, compare what I have to yours (if you have one).  Like I said, I got this from a website.  It may not be legit (structurally).  Check it closely, please.

There is still a problem .. neither Xsane or Simple scan finds the device.  I tried running from GUI and ```
sudo xsane
```.  I even did a machine restart and tried them again .. both ways.

Also, now I am not getting that Xsane splash screen.

---

### Post by Jose Catre-Vandis on 2011-07-09
I think DEVICE needs to be the name on the printer:

```
DEVICE=MFC-7440N **not** DEVICE=SCANNER
```

so you need to do the scanner initialisation again with:

```
brsaneconfig3 -a MODEL=MFC-7440N NAME=MFC-7440N ip=192.168.0.8
```

---

### Post by jfbooth on 2011-07-09
> **Jose Catre-Vandis said:**
> I think DEVICE needs to be the name on the printer:

```
DEVICE=MFC-7440N **not** DEVICE=SCANNER
```

so you need to do the scanner initialisation again with:

```
brsaneconfig3 -a MODEL=MFC-7440N NAME=MFC-7440N ip=192.168.0.8
```

OK .. here is the content of brsanenetdevice3.cfg:

```
DEVICE=MFC=7440N , "MFC-7440N" , 0x4f9:0x1e6 , IP-ADDRESS=192.168.001.008
```

Here is the output from ```
jb@Backroom-Linux:~$ sudo brsaneconfig3 -a MODEL=MFC-7440N NAME=MFC-7440N ip=192.168.0.8
[sudo] password for jb: 
**Invalid name**
```

Again, here is /lib/udev/rules.d/40-libsane.rules.  I changed ```
LABEL="libsane_**scsi**_rules_end"
``` to ```
LABEL="libsane_**usb**_rules_end"
``` because **scsi** did not look right.


```
# This file was automatically created based on description files (*.desc)
# by sane-desc 3.5 from sane-backends 1.0.22 on Wed Mar 23 19:05:11 2011
#
# udev rules file for supported USB and SCSI devices
#
# The SCSI device support is very basic and includes only
# scanners that mark themselves as type "scanner" or
# SCSI-scanners from HP and other vendors that are entitled "processor"
# but are treated accordingly.
#
# To add a USB device, add a rule to the list below between the
# LABEL="libsane_usb_rules_begin" and LABEL="libsane_usb_rules_end" lines.
#
# To run a script when your device is plugged in, add RUN+="/path/to/script"
# to the appropriate rule.
#
# If your scanner isn't listed below, you can add it as explained above.
#
# If your scanner is supported by some external backend (brother, epkowa,
# hpaio, etc) please ask the author of the backend to provide proper
# device detection support for your OS
#
# If the scanner is supported by sane-backends, please mail the entry to
# the sane-devel mailing list (sane-devel@lists.alioth.debian.org).
#
ACTION!="add", GOTO="libsane_rules_end"
ENV{DEVTYPE}=="usb_device", GOTO="libsane_create_usb_dev"
SUBSYSTEMS=="scsi", GOTO="libsane_scsi_rules_begin"
SUBSYSTEM=="usb_device", GOTO="libsane_usb_rules_begin"
SUBSYSTEM!="usb_device", GOTO="libsane_usb_rules_end"

# Kernel >= 2.6.22 jumps here
LABEL="libsane_create_usb_dev"

# For Linux >= 2.6.22 without CONFIG_USB_DEVICE_CLASS=y
# If the following rule does not exist on your system yet, uncomment it
# ENV{DEVTYPE}=="usb_device", MODE="0664", OWNER="root", GROUP="root"

# Kernel < 2.6.22 jumps here
LABEL="libsane_usb_rules_begin"

# Brother MFC-7440N
SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="01e6", MODE="664", GROUP="scanner"

ENV{libsane_matched}=="yes", RUN+="/bin/setfacl -m g:scanner:rw $env{DEVNAME}"

LABEL="libsane_usb_rules_end"
```

Now, running XSANE returns nothing .. literally.  Window opens "scanning for device' and then closes.  No error.  Running Simple Scan returns "Failed to open device 'brother3:net1;dev0': Invalid argument.

---

### Post by Jose Catre-Vandis on 2011-07-09
> **jfbooth said:**
> OK .. here is the content of brsanenetdevice3.cfg:

```
DEVICE=MFC**=**7440N , "MFC-7440N" , 0x4f9:0x1e6 , IP-ADDRESS=192.168.001.008
```


Check your = should be a - in DEVICE=MFC=7440N

---

### Post by jfbooth on 2011-07-09
DUH.  Sorry about that.  Here is the corrected content:

```
DEVICE=MFC-7440N , "MFC-7440N" , 0x4f9:0x1e6 , IP-ADDRESS=192.168.001.008
```

To my surprise, **/lib/udev/rules.d/40-libsane.rules** was GONE.  Worse, I do not have the copy I downloaded so I created my own from memory.  Here is the content of /lib/udev/rules.d/40-libsane.rules

```
ACTION!="add", GOTO="libsane_rules_end"
ENV{DEVTYPE}=="usb_device", GOTO="libsane_create_usb_dev"
SUBSYSTEMS=="scsi", GOTO="libsane_scsi_rules_begin"
SUBSYSTEM=="usb_device", GOTO="libsane_usb_rules_begin"
SUBSYSTEM!="usb_device", GOTO="libsane_usb_rules_end"

# Kernel >= 2.6.22 jumps here
LABEL="libsane_create_usb_dev"

# For Linux >= 2.6.22 without CONFIG_USB_DEVICE_CLASS=y
# If the following rule does not exist on your system yet, uncomment it
# ENV{DEVTYPE}=="usb_device", MODE="0664", OWNER="root", GROUP="root"

# Kernel < 2.6.22 jumps here
LABEL="libsane_usb_rules_begin"

# Brother MFC-7440N
SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="01e6", MODE="664", GROUP="scanner"

ENV{libsane_matched}=="yes", RUN+="/bin/setfacl -m g:scanner:rw $env{DEVNAME}"

LABEL="libsane_usb_rules_end"
```

PLEASE verify this is all correct.  I think there should be more to it because even after correcting **brsanenetdevice3.cfg** XSANE still fails with "Invalid Argument".  

I remind you, all this started when lsusb did not return Product/Vendor IDs and I had no 40-libsane.rules file to append to.

---

### Post by Jose Catre-Vandis on 2011-07-09
1. The device IDs won't show in with lsusb because its a network device, has to be connected via a usb interface to do this. Just appears to be an odd quirk that you "may" need the entry.

2. I attach my 40-libsane.rules for you from my 11.04 Xubuntu install. I notice that all the entries have a different format, so it is worth trying:```

#Brother MFC-7440N
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="01e6", ENV{libsane_matched}="yes"
``` either instead of or as well as the first entry you have tried.

[ATTACH]197077[/ATTACH]

Other than that I am stumped. Having googled, others have this machine working on Ubuntu but no-one give a clear cut how to on how they did it which indicates the standard setup as shown on the Brother site does work. Have a good search on the forum for other ideas, there are plenty of Brother how tos scattered about.

---

### Post by jfbooth on 2011-07-09
I cannot thank you enough for all your valuable time.  I took your 40-libsane.rules file and added ```
#Brother MFC-7440N
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="01e6", ENV{libsane_matched}="yes"
``` to it.  I hope I put it in the right place.  Here is what I have in summary:

```
ACTION!="add", GOTO="libsane_rules_end"
ENV{DEVTYPE}=="usb_device", GOTO="libsane_create_usb_dev"
SUBSYSTEMS=="scsi", GOTO="libsane_scsi_rules_begin"
SUBSYSTEM=="usb_device", GOTO="libsane_usb_rules_begin"
SUBSYSTEM!="usb_device", GOTO="libsane_usb_rules_end"

# Kernel >= 2.6.22 jumps here
LABEL="libsane_create_usb_dev"

# For Linux >= 2.6.22 without CONFIG_USB_DEVICE_CLASS=y
# If the following rule does not exist on your system yet, uncomment it
# ENV{DEVTYPE}=="usb_device", MODE="0664", OWNER="root", GROUP="root"

# Kernel < 2.6.22 jumps here
LABEL="libsane_usb_rules_begin"

# Hewlett-Packard ScanJet 4100C
ATTRS{idVendor}=="03f0", ATTRS{idProduct}=="0101", ENV{libsane_matched}="yes"
# Hewlett-Packard ScanJet 6300C
KERNEL=="sg[0-9]*", ATTRS{type}=="3", ATTRS{vendor}=="HP", ATTRS{model}=="C7670A", ENV{libsane_matched}="yes"
#Brother MFC-7440N
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="01e6", ENV{libsane_matched}="yes"

LABEL="libsane_scsi_rules_end"

ENV{libsane_matched}=="yes", RUN+="/bin/setfacl -m g:scanner:rw $env{DEVNAME}"

LABEL="libsane_rules_end"
```

It just doesn't look right to me.  Seems to be in a SCSI section.  Also, I'm wondering if line 10 needs to be uncommented.

In any case. it is still not working.  I am very close to installing from scratch .. Xubuntu 11.04 and (I guess) this time, NOT use the 'TUTORIAL' but the instructions at BROTHER website.  I will await your final comment, and then, if no change, do that.

Finally, THANK YOU immensely for all you have done.  Much appreciated.

EDIT:  What has me perplexed is with XUBUNTU 10/10, the _tutorial_ worked.  lsusb returned what I needed.  Scanner and printer were working within 20 minutes.  This is why I referred to the tutorial THIS time, and just about NOTHING went right.  I just hope going the Brother route is straight forward and works.  Thanks again.

---

### Post by jfbooth on 2011-07-10
None of it really matters.  I installed Xubuntu 11.04 from CD ... wiped hard disk.  I completely started over but this time did NOT go by the 'tutorial'.  I went entirely by the Brother website.  To be honest, that procedure is VASTLY different from the 'tutorial'.  Sad thing is, though different, and I was VERY diligent, it still will not scan.  I carefully performed all the prerequisites, and installed the software exactly as instructed.  Even VERIFIED the installations with there 'verify' instructions.  Printer works great.  Xsane nor Simple Scan will see the scanner.  My only hope is someone will help out because I am stumped .. and I understand Jose Catre-Vandis may be also .. or is burnt out on helping (I don't blame him one bit).

---

### Post by Jose Catre-Vandis on 2011-07-10
Did you try the new install with **sudo xsane** ?

---

### Post by jfbooth on 2011-07-10
> **Jose Catre-Vandis said:**
> Did you try the new install with **sudo xsane** ?

yes, with the same results as from the GUI.  Small window opens "searching for device' (or something like that) .. then that window closes.  No 'splash screen'.  Then, after a 'while', window pops up "Failed to open device 'brother3:net1;dev0': Invalid argument".

Dunno if it helps, but here is what I did.  Fresh install of Xubuntu 11.04.  Downloaded 3 files from Brother site .. all for MFC-7440N (networked).

brmfc7440nlpr-2.0.2-1.i386.deb
brscan3-0.2.11-4.i386.deb
cupswrapperMFC7440N-2.0.2-1.i386.deb

I read the PREREQUISITES for each. Here they are for the SCANNER:

Pre-required Procedure (8)
    Related distributions
    Debian, Ubuntu
    Related products/drivers
    brscan, brscan2, brscan3
    Requirement
    sane-utils is required to be installed.

sane-utils was/is installed.

Here are instructions for install:

Step 4. Install the driver
    4-1. Turn on your MFC/DCP and connect to the network.
    4-2. Open the terminal and go to the directory where the driver is.
    4-3. Install the scanner driver

        Command (for dpkg)  :  dpkg  -i  --force-all  (scanner-drivername)
        
    4-4. Check if the driver is installed

        Command (for dpkg)  :  dpkg  -l  |  grep  Brother
        
Step 5. Setting for your network scanner
    ***Use brsaneconfig (for brscan models), brsaneconfig2 (for brscan2 models) or brsaneconfig3 (for brscan3 models) accordingly.
    5-1. Add network scanner entry

        Command  :  brsaneconfig2  -a  name=(name  your  device)  model=(model  name)  ip=xx.xx.xx.xx
        
    5-2. Confirm network scanner entry

        Command  :  brsaneconfig2  -q  |  grep  (name  of  your  device)
        
Step 6. Try a test scan
    6-1. Open a scanner application and try a test scan.

I did all that, and here is the confirmation:

```
jb@Compaq:~$ brsaneconfig3 -q | grep MFC-7440N
 91 "MFC-7440N"
  0 SCANNER             "MFC-7440N"         I:192.168.001.008
jb@Compaq:~$
```

There is no mention of lsusb or 40-libsane.rules in any of the BROTHER procedures for a NETWORKED MFC-7440N printer/scanner.  Printer works 'fine'.  Just no SCAN.

---

### Post by Jose Catre-Vandis on 2011-07-10
Try
```
sudo -i
``` (enter password if asked)
then
```
xsane
```

Possible that device 3 has root permissions only, so just using sudo isn't good enough. If this works, you'll have to change the permissions on the device. Open "dev/bus/usb/004" as root and check permissions on device 3 (003 file). Change to your user and try again? 

Also try uninstalling the brscan3 driver and reinstalling it

---

### Post by jfbooth on 2011-07-10
> **Jose Catre-Vandis said:**
> Try
```
sudo -i
``` (enter password if asked)
then
```
xsane
```

No change.

> Also try uninstalling the brscan3 driver and reinstalling it

OK, .. I did:

```
jb@Compaq:~/Desktop$ sudo dpkg  -i  --force-all  brscan3-0.2.11-4.i386.deb
[sudo] password for jb: 
Selecting previously deselected package brscan3.
(Reading database ... 129467 files and directories currently installed.)
Unpacking brscan3 (from brscan3-0.2.11-4.i386.deb) ...
Setting up brscan3 (0.2.11-4) ...
jb@Compaq:~/Desktop$ dpkg  -l  |  grep  Brother
ii  brmfc7440nlpr                        2.0.2-1                                    Brother MFC-7440N LPR driver
ii  brscan3                              0.2.11-4                                   Brother Scanner Driver
ii  cupswrappermfc7440n                  2.0.2-1                                    Brother MFC7440N CUPS wrapper driver
jb@Compaq:~/Desktop$
```

Then I ran XSANE from the GUI (no sudo).  DIFFERENT BEHAVIOR this time.  Small window pops up,  "Scanning for Devices" then another window "No Devices Available".  In the past, different windows would pop up .. like 'invalid argument' for example.

I wonder if I missed a prerequisite at the Brother Site.  I don't think I did .. there was only one that I saw .. **sane-utils is required to be installed**..but here is a link to that info (click on link, scroll UP on the new page, see "Step 2. Check if pre-required procedures are completed":

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1b.html#dpkg2]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1b.html#dpkg2")

Edit:  I also tried:

```
jb@Compaq:~$ sudo -i
[sudo] password for jb: 
root@Compaq:~# xsane
root@Compaq:~#
```

again .. no change.

---

### Post by jfbooth on 2011-07-15
**Jose Catre-Vandis**

First of all, I want to thank you IMMENSELY for all your help.

I FINALLY figured out the problem .. just now.

When I got to the step:

```
Command  :  brsaneconfig3  -a  name=(name  your  device)  model=(model  name)  ip=xx.xx.xx.xx
```

I realized I needed to know the IP address.  Grabbed USER GUIDE and it said to make certain selections on the device LCD menu.  I did and it returned

**IP-ADDRESS=192.168.001.008**

so that is what I used.  I edited the **brsanenetdevice3.cfg** file for an IP of **192.168.1.8** and it is working beautifully!!!

Again, THANK YOU for all your help.

---

### Post by Jose Catre-Vandis on 2011-07-15
Well done m8 - we should both have spotted that earlier!

Glad you have it working, and now a full repertoire of tests and fixes all ready for the next upgrade to 11.10 ;)

---

