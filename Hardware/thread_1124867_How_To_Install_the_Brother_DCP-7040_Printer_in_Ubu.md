---
title: "How To: Install the Brother DCP-7040 Printer in Ubuntu 8.10"
date: 2009-04-13
forum: Hardware
---

### Post by Floppyjoe on 2009-04-13
**How To: Install the Brother DCP-7040 Printer in Ubuntu 8.10 32bit**


1).** First you need to download the drivers that you need for the installation.**
The best place to get them is the manufacturers [site](http://solutions.brother.com/linux/en_us/index.html).
**The Print Drivers**
[DCP-7040 lpr driver 32bit](http://solutions.brother.com/Library/sol/printer/linux/dlf/brdcp7040lpr-2.0.2-1.i386.deb)
[DCP-7040 cupswrapper driver](http://solutions.brother.com/Library/sol/printer/linux/dlf/cupswrapperDCP7040-2.0.2-1.i386.deb)
**And the Scanning Drivers**
[brscan3 32bit driver](http://solutions.brother.com/Library/sol/printer/linux/dlf/brscan3-0.2.5-2.i386.deb)
[brscan-skey driver](http://solutions.brother.com/Library/sol/printer/linux/dlf/brscan-skey-0.2.1-3.i386.deb)
**Pre-Install procedure for cups printer driver**
a.) Open a terminal by clicking on Applications/Accessories/Terminal and type in the following commands
> sudo aa-complain cupsd
> sudo mkdir /usr/share/cups/model

2.)**Install the LPR and Cupswrapper drivers**
a.) Open a Terminal again and CD(change directory) to where the drivers are stored on your computer.
b.) Install the LPR driver:
> sudo dpkg  -i  --force-all  --force-architecture  (lpr-drivername)
where the part in brackets is the name of the file you downloaded.
c.) Install the Cupswrapper driver:
> sudo dpkg  -i  --force-all  --force-architecture  (cupswrapper-drivername)
where the part in brackets is the name of the other driver you downloaded.

3.) **Check if the drivers installed correctly**
> sudo dpkg  -l  |  grep  Brother

4.)**For a USB Printer: Check your printer on the cups web interface**
Open a web browser and go to "http://localhost:631/printers".

    Check if the Device URI of your printer is "usb://Brother/DCP-7040" 
    
    If the device URI is different from the example above, please go to "Modify Printer" of your printer to select proper device and driver.

    If your printer is not listed on "http://localhost:631/printers", please go to "http://localhost:631/admin" and click "Add printer" and select proper device and driver. 

The correct PPD file will be in the folder /usr/share/cups/model.

5.)**(for Network Connection) Configure your printer on the cups web interface**
    Open a web browser and go to "http://localhost:631/printers". 
    Click "Modify Printer" and set following parameters.

    - LPD/LPR Host or Printer 	     	for Device
    - lpd://(Your printer's IP address)/binary_p1 	     	for Device URI
    - Brother 	     	for Make/Manufacturer Selection
    - Your printer's name 	     	for Model/Driver Selection
    Note for Ubuntu8.10: Please set "AppSocket/HP JetDirect" for Device menu

**Now try a test printing**

6.)**Enable the scanner features of the DCP-7040**
a.) open a terminal and enter the following:
> sudo apt-get install sane-utils
b.) CD to where the drivers are stored on your computer.
> sudo dpkg  -i  --force-all  (scanner-drivername)
where the part in brackets is the file name of the scanner driver 32 bit file.
> sudo dpkg  -i  --force-all  (scan-key-toolname)
where the part in brackets is the scan key tool driver file.
c.) Check if these installed correctly
> sudo dpkg  -l  |  grep  Brother
d.) Change some values in a config file
>  sudo gedit /etc/udev/rules.d/40-basic-permissions.rules
    Edit "0664" to "0666" in "USB devices" section.

    Before the edit---------------------------------

    # USB devices (usbfs replacement)
    SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0664"
    SUBSYSTEM=="usb_device",                MODE="0664"

    After the edit----------------------------------

    # USB devices (usbfs replacement)
    SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0666"
    SUBSYSTEM=="usb_device",                MODE="0666"

7.)** Restart the OS.**

---

### Post by nuclearlee on 2009-12-15
AWESOME!  I had all but given up with printing.

I am using Kubuntu Karmic and impatiently followed the steps to step 4 (checking local host to see if there was a printer).  Didn't bother reading the rest of the directions past that.  After checking to see if there was a printer, I was able to print no problem!  THANKS!!!!

---

### Post by jbatista on 2010-05-26
Floppyjoe, thanks for the precious walkthrough!

> sudo gedit /etc/udev/rules.d/40-basic-permissions.rules 

On Ubuntu Lucid (10.04), the file above no longer exists. However, a similar file with the two affected entries is instead **/lib/udev/rules.d/50-udev-default.rules**
As always, think twice before you edit and make backups of the affected files.

HTH.

---

### Post by masticate on 2010-07-15
To modify the files for scanning in Ubuntu 10.4, Brother states

> 
[LIST=1]
[*]Open "/lib/udev/rules.d/40-libsane.rules" file.
[*]Add the following two lines to the end of the device list. (Before the line "# The following rule will disable ..."):


The lines to be added---------------------------
```

# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"

```
[*]Restart the OS.
[/LIST]


Resource:
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u9.10]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u9.10")

---

### Post by bedihardeep on 2010-10-27
hello there i did almost everything except 

when i run that command 
"sudo gedit /etc/udev/rules.d/40-basic-permissions.rules"

that file opens but its blank i was unable to find parameters that has to be replaced 

please reply your feedback is greatly appreciated

---

### Post by bedihardeep on 2010-10-28
> **Floppyjoe said:**
> **How To: Install the Brother DCP-7040 Printer in Ubuntu 8.10 32bit**


1).** First you need to download the drivers that you need for the installation.**
The best place to get them is the manufacturers [site]("http://solutions.brother.com/linux/en_us/index.html").
**The Print Drivers**
[DCP-7040 lpr driver 32bit]("http://solutions.brother.com/Library/sol/printer/linux/dlf/brdcp7040lpr-2.0.2-1.i386.deb")
[DCP-7040 cupswrapper driver]("http://solutions.brother.com/Library/sol/printer/linux/dlf/cupswrapperDCP7040-2.0.2-1.i386.deb")
**And the Scanning Drivers**
[brscan3 32bit driver]("http://solutions.brother.com/Library/sol/printer/linux/dlf/brscan3-0.2.5-2.i386.deb")
[brscan-skey driver]("http://solutions.brother.com/Library/sol/printer/linux/dlf/brscan-skey-0.2.1-3.i386.deb")
**Pre-Install procedure for cups printer driver**
a.) Open a terminal by clicking on Applications/Accessories/Terminal and type in the following commands



2.)**Install the LPR and Cupswrapper drivers**
a.) Open a Terminal again and CD(change directory) to where the drivers are stored on your computer.
b.) Install the LPR driver:

where the part in brackets is the name of the file you downloaded.
c.) Install the Cupswrapper driver:

where the part in brackets is the name of the other driver you downloaded.

3.) **Check if the drivers installed correctly**


4.)**For a USB Printer: Check your printer on the cups web interface**
Open a web browser and go to "http://localhost:631/printers".

    Check if the Device URI of your printer is "usb://Brother/DCP-7040" 
    
    If the device URI is different from the example above, please go to "Modify Printer" of your printer to select proper device and driver.

    If your printer is not listed on "http://localhost:631/printers", please go to "http://localhost:631/admin" and click "Add printer" and select proper device and driver. 

The correct PPD file will be in the folder /usr/share/cups/model.

5.)**(for Network Connection) Configure your printer on the cups web interface**
    Open a web browser and go to "http://localhost:631/printers". 
    Click "Modify Printer" and set following parameters.

    - LPD/LPR Host or Printer              for Device
    - lpd://(Your printer's IP address)/binary_p1              for Device URI
    - Brother              for Make/Manufacturer Selection
    - Your printer's name              for Model/Driver Selection
    Note for Ubuntu8.10: Please set "AppSocket/HP JetDirect" for Device menu

**Now try a test printing**

6.)**Enable the scanner features of the DCP-7040**
a.) open a terminal and enter the following:

b.) CD to where the drivers are stored on your computer.

where the part in brackets is the file name of the scanner driver 32 bit file.

where the part in brackets is the scan key tool driver file.
c.) Check if these installed correctly

d.) Change some values in a config file

    Edit "0664" to "0666" in "USB devices" section.

    Before the edit---------------------------------

    # USB devices (usbfs replacement)
    SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0664"
    SUBSYSTEM=="usb_device",                MODE="0664"

    After the edit----------------------------------

    # USB devices (usbfs replacement)
    SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0666"
    SUBSYSTEM=="usb_device",                MODE="0666"

7.)** Restart the OS.**

hello there i did almost everything except 

when i run that command 
"sudo gedit /etc/udev/rules.d/40-basic-permissions.rules"

that file opens but its blank i was unable to find parameters that has to be replaced 

please reply your feedback is greatly appreciated

---

### Post by gimfred on 2010-12-25
@bedihardeep:

The obvious is to create the file. 

sudo gedit /etc/udev/rules.d/40-basic-permissions.rules &

```
# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0666"
SUBSYSTEM=="usb_device", MODE="0666"
```

copy and paste into the file and save.

However the share printer and scanner still didnt work for me

---

### Post by Jim_in_Omaha on 2011-01-07
> **gimfred said:**
> @bedihardeep:

The obvious is to create the file. 

sudo gedit /etc/udev/rules.d/40-basic-permissions.rules &

```
# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0666"
SUBSYSTEM=="usb_device", MODE="0666"
```

copy and paste into the file and save.

However the share printer and scanner still didnt work for me

This procedure worked for me on a DCP-7040 on 10.10 64-bit MM and I had to add this to the 40-basic-permissions.rules

---

### Post by lagom on 2011-01-21
Hi, 

I followed the instructions above and successfully installed both the scanner and printer from the 7040. Yesterday I tried to print a couple of pages and couldn't figure out how to tell my printer that it should print two-sided/duplex. 

Any Ideas how to go about that? Am I right in assuming that this function is not included in this driver?

Thanks for answering!

=)

Salome

---

### Post by gleedadswell on 2011-04-29
I'm running

Linux geoff-laptop 2.6.32-30-generic #59-Ubuntu SMP Tue Mar 1 21:30:46 UTC 2011 x86_64 GNU/Linux

on a Lenovo laptop.  The procedure above (using the drivers from the Brother website) didn't work.  I got the problem that when I submitted a job the printer display would show "Receiving Data" but nothing else would happen.  CUPS would report a successful print even though no printing took place.:confused:

I then installed the Brother printer drivers from the Ubuntu repos using Synaptic (this operation failed until I removed the drivers from Brother - for those of you with relatively little linux experience this is probably most easily done using dpkg -r).  I think the crucial package was

brother-lpr-drivers-laser

Once I had done this and reinstalled the printer using the Brother DCP-7020 Foomatic/hl1250 driver that I now had available the printer worked immediately.:p

My general experience is that device drivers made for linux provided by commercial vendors are very hit and miss.  But any drivers from the repos are likely to work with no problem.  In this case a contributing factor was probably that I'm running 64-bit and the Brother supplied driver is definitely for 32-bit which is why you need to use the --force flag in dpkg -i when you install the Brother driver.  From comments above it looks like the Brother driver worked for some other people running 64-bit Ubuntu.  Maybe the difference in my case was a laptop hardware issue??  Or maybe it is to do with subtle differences between Ubuntu 8 and Ubuntu 10??

So far I've only got the printer running.  I'll post back once I've tried to get the scanner working.

---

### Post by Jim_in_Omaha on 2011-04-30
Exact same problem here with the 7040 and scanning. Will subscribe to this post.

---

### Post by graphius on 2011-05-03
scanning works fine, it is the printing part I am having a problem with.
Apparently there has been a but with 32-bit and 64-bit drivers for a while 
[brother-lpr-drivers-laser/+bug/769241]("https://bugs.launchpad.net/ubuntu/+source/brother-lpr-drivers-laser/+bug/769241")

EDIT
> then installed the Brother printer drivers from the Ubuntu repos using Synaptic (this operation failed until I removed the drivers from Brother - for those of you with relatively little linux experience this is probably most easily done using dpkg -r). I think the crucial package was

brother-lpr-drivers-laser

Once I had done this and reinstalled the printer using the Brother DCP-7020 Foomatic/hl1250 driver that I now had available the printer worked immediately.

Printer works great using the 7020 driver

---

### Post by Jim_in_Omaha on 2011-05-13
> **Jim_in_Omaha said:**
> Exact same problem here with the 7040 and scanning. Will subscribe to this post.

I fixed my DCP-7040 scanning problem. Turned out to be the rights issue for the USB. If I ran 'sudo simple-scan' (run as root) it works. There is no scanner group in my 11.04 groups. So instead I just simply set the usb/dev for the scanner to 777. 

Found it by:

typing 'sane-find-scanner'

which displayed this info
found USB scanner (vendor=0x04f9, product=0x01e9) at libusb:004:003

then went to and set the permissions for this device with
'sudo chmod 777 /dev/bus/usb/004/003'

and now it works wonderfully. I could not find where to fix the 'scanner' group not being there. But all is good in the 11.04 world now that my DCP-7040 is fully functional again. Probably not the best and secure way to fix it in a multi-user environment. And input on the 'scanner' group for Natty would be appreciated.

---

### Post by gleedadswell on 2012-01-14
The last time I posted here I was running 10.10 on a Lenovo laptop.  Now I'm getting this printer working for the first time under 11.10 on an HP 2000 laptop.

When I plugged the printer in CUPS immediately recognized it and configured it.  But when I tried to print I got the same behaviour that I've seen before: CUPS reports the job sent, the printer's display reports "receiving data", then CUPS reports that the job is completed even though no printing actually happened.  I opened CUPS to reconfigure the printer.  It had selected the "Brother DCP-7045N foomatic" driver.  I changed this to the "Brother DCP-7020 Foomatic/hl1250" driver that worked for me before.

Voila!  Now it works...as a printer.

Simple Scan reports no scanner detected.  Running sane-find-scanner reports:

found USB scanner (vendor=0x04f9, product=0x01e9) at libusb:003:005
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

But after this Simple Scan still can't find it.

Last time I did this I tried scanner drivers from the repos and they didn't work.  Eventually I used the Brother software (which I'm surprised to see they are distributing under GNU pulic licence...).  So this time I decided to go straight to that route.  I first checked and saw that I'm running 32 bit.  So I went to 

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)

and grabbed the appropriate scanner driver and scan key tool.  The instructions there are fairly clear, and they've been summarized in this thread already by floppyjoe.  Don't miss the part of the instructions about how to make the scanner available to normal users, which is linked from the page of instructions for installing the scanner driver.  It involves editing 

/etc/udev/rules.d/60-libsane.rules

Happy scanning!

---

### Post by gleedadswell on 2012-01-31
...and a further update.

At the time of my previous post I was mostly just setting the printer up on that computer to do scanning.  So when the printer gave me a good test page I foolishly assumed that the printing was fully functional and went on to deal with the setting up the scanning.

Now I've set this printer up as the main printer on another computer running Ubuntu 11.10.  When I set it up I had the usual symptom (doesn't print with the automatically selected DCP-7045 driver, gives a good test page with the DCP-7020 driver).  But when I printed a real document from Open Office Writer it had all sorts of little black rectangles at the bottoms of descenders on letters (i.e. at the bottoms of any "p", "g", "q", "j", etc.).

Reading my previous previous post I recalled the need to install brother-lpr-drivers-laser.  Having done that I selected the new driver available "DCP-7020 for CUPS".  This immediately fixed the problem.

Does anyone know why there is no DCP-7040 driver and we always seem to need to use the 7020 driver for this printer?

---

### Post by graphius on 2012-01-31
> all sorts of little black rectangles at the bottoms of descenders on letters (i.e. at the bottoms of any "p", "g", "q", "j", etc.).

If you turn off economy mode, or at least change it from high to low, the print quality improves drastically.

---

### Post by graphius on 2012-02-06
and after following all this thread, I still can't get it to scan...

Do you have to do anything to the printer itself?

PS printing has always worked fine...

---

