---
title: "v14 already and -still- no proper printer installation support"
date: 2016-04-01
forum: Hardware
---

### Post by rumplestilts on 2016-04-01
Sorry if this is viewed as complaining but I guess it is.

For years I've been trying to like Ubuntu but every time I install it on any of my machines (Macs or PCs), I end up wiping the drive and going back to OSX or Windows. Why? Only one reason: I never can get printing to work. Maybe it's because I use Brother printers; I just can't figure it out.

The latest example: I have a MacBook on which I've installed the LTS 14 version (14.04?). No problem so far. But I simply can't find a way to get the machine to print to my Brother MFC-J6710DW inkjet printer. Ubuntu sees the printer and even suggests using a "generic" driver for text-only printing (but even that never works). The strange thing is that I -can- print if I select the same printer I share from my Mac (running OSX). Then printing works exactly as one would wish. But I don't want to -have- to keep that Mac powered up in order to print from the Ubuntu device (the MacBook).

I'd love to know how I can get this working properly. Does anyone have a good set of directions that doesn't involve "then a miracle happens"? ;)

Thanks,
Barry

---

### Post by davidvandoren on 2016-04-02
Go to [http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=mfcj6710dw_all&os=128](http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=mfcj6710dw_all&os=128)
Download the driver install tool and run it in the terminal. 

Or download each driver and install them one by one. 
Brother has linux drivers for all their printers.

---

### Post by ian-weisser on 2016-04-02
> **rumplestilts said:**
> Maybe it's because I use Brother printers

Manufacturer's fault. Complain to them.
Brother does not contribute the neccessary software to make their products work out-of-the-box, and licenses their software to prohibit community users from doing it for them.

You are paying Brother for the feature of being not-easily-compatible. Consider changing your brand loyalty.

---

### Post by rumplestilts on 2016-04-03
David, Ian,

Thanks for your suggestions. I did try David's suggestion already and it was not successful. Not sure why my machine can't connect to my printer over my network yet it -can- connect to the -shared- printer (shared from my Mac running OSX). It's CUPS so what's the problem?

I'll complain to Brother (yet again) but they treat complaints from Linux users like they -used- to treat complaints from Mac users before Apple adopted CUPS. Once Apple embraced CUPS, all printer issues vanished (for me, anyway, on my Mac).

---

### Post by ian-weisser on 2016-04-04
> **rumplestilts said:**
> It's CUPS so what's the problem?

If it connects to the printer via a share, then CUPS seems to be working.
Could be your network.
Could be that the printer is not in network mode.
Could be you are inputting a typo or the wrong ip address.
Could be that you previously set up a firewall rule that blocks Bonjour, so the printer announcements are blocked.
Could be that you previously uninstalled Bonjour for some reason.
Could be lots of possiblilities

Start simply. Reboot your system, and try to connect to your printer's IP address.

If that doesn't work, then please lead us through the exact process you are using to try and detect the printer. We may not be using the same version of Ubuntu or CUPS that you are, so please be verbose.

---

### Post by rumplestilts on 2016-04-05
Ian,

Hopefully this will answer your post in a way that makes sense.

- Network: All devices on my local network are connected to an AT&T Uverse gateway (although there's a gigabit switch in one of the gateway's ports to which some devices are also connected but this is a dumb switch so nothing is blocked/blocking). None of my computers have their firewall turned on. The Mac mini has printer sharing on and the Brother printer is connected to it via USB. All other devices (other Macs, PCs, Nexus 5 phone) communicate with the printer via the gateway's WiFi. The Brother printer is connected to the network via Ethernet (directly to the gateway). [Brother printers can have both USB and Networking active simultaneously.]
- So the Printer is in "network mode".
- IP is 192.168.1.87 (via DHCP).
- No firewall rules.
- Uninstalled nothing after the initial Ubuntu installation (which included updates).

I will post again in an hour or so once I finish re-installing Ubuntu (a fresh install on an initialized HD) and go through the procedure of attempting to install the printer.

By the way: In most of my previous attempts I know I was connecting to the printer because I saw the printer's status screen light up and even occasionally show "receiving data". But in all cases, the status screen went back to the "resting state" (for want of a better phrase) without printing anything. So I'm thinking this may be just a driver issue (but Brother's driver support is laughable).

Will be back soon.

Thanks,
Barry

---

### Post by rumplestilts on 2016-04-05
Here's my printer's network configuration. Perhaps that will provide other info that would help you suggest what sort of configuration I need to craft in my Ubuntu installation.

[ATTACH=CONFIG]268199[/ATTACH]

---

### Post by rumplestilts on 2016-04-05
When I add a Network Printer, my Brother printer shows up twice - once with the NetBIOS/Node name and once with "BRN001..." and its IP address. I've selected the latter (the Description Ubuntu provides is "IPP network printer via DNS-SD". I click the "Forward" button. Ubuntu suggests I select "Generic, Text-only" and, when I do and I'm asked if I want to print a test page, I confirm and then receive a "CUPS server error: 'client-error-document-format-not-supported'.

So I delete that printer from the queue and go back to square one. Tries another dozen choices and, in each case, the printer's status screen lights briefly and that's all.

I went to the Brother webpage (linked in an earlier post) and found these instructions:
> **How to Install**

    
[LIST]
[*]    Login as a superuser ( or use "sudo" option if it is required ) 
[*]    Check if pre-required procedures are completed
   [**For Debian/Ubuntu 64 bit**]("http://support.brother.com/g/s/id/linux/en/before.html#004")
   [**For Ubuntu8.04 or greater**]("http://support.brother.com/g/s/id/linux/en/before.html#002") 
[*]    Download drivers
   [Download LPR driver]("http://support.brother.com/g/b/link.aspx?os=128&type3=559") and cupswrapper driver. 
[*]    Install LPR driver and cupswrapper driver
[LIST]
[*]      Turn on the printer and connect the USB cable. 
[*]      Open the terminal and go to the directory where the drivers are. 
[*]      Install LPR driver.The install process may take some time. Please wait until it is complete.
     **Command (for dpkg)  :  dpkg  -i  --force-all  (lpr-drivername)** 
[*]      Install cupswrapper driver.The install process may take some time. Please wait until it is complete.
     **Command (for dpkg)  :  dpkg  -i  --force-all  (cupswrapper-drivername)** 
[*]      Check if the LPR driver and cupswrapper driver are installed
     **Command (for dpkg)  :  dpkg  -l  |  grep  Brother** 
[/LIST]
  
[*]    Depending on the connection type you are using (USB or Network), follow one of the steps below.
   
   _**(for USB Connection)**_
[LIST]
[*]      Open a web browser and go to **"http://localhost:631/printers"**. 
[*]      Check if the Device URI of your printer is **"usb://Brother/(your printer's model name)"**
     
     If the device URI is different from the example above, please go to  "Modify Printer" of your printer to select proper device and driver.
     If your printer is not listed on "http://localhost:631/printers", please go to **"http://localhost:631/admin"** and click "Add printer" and select proper device and driver. 
[/LIST]
          
    _**(for Network Connection)**_          
    
[LIST]
[*]      Open a web browser and go to **"http://localhost:631/printers"**. 
[*]      Click "Modify Printer" and set following parameters.
     [TABLE]
[TR]
[TD]          - "LPD/LPR Host or Printer" or "AppSocket/HP JetDirect"[/TD]
[TD][/TD]
[TD]          for Device[/TD]
[/TR]
[TR]
[TD]          - lpd://(Your printer's IP address)/binary_p1[/TD]
[TD][/TD]
[TD]          for Device URI[/TD]
[/TR]
[TR]
[TD]          - Brother[/TD]
[TD][/TD]
[TD]          for Make/Manufacturer Selection[/TD]
[/TR]
[TR]
[TD]          - Your printer's name
[/TD]
[TD][/TD]
[TD]          for Model/Driver Selection[/TD]
[/TR]
[/TABLE] 
[/LIST]
  
[*]    Try a test print
   Open a text editor, write something and select "print" from the menu. 
[/LIST]
 


After reading that I'm loading a gun and preparing to shoot the screen.

Edit: "Your printer's name" - which one of the names might that be?

---

### Post by rumplestilts on 2016-04-05
Downloaded and installed both the CUPSwrapper and LPD files for the MFC-J6720DW from the linked webpage. Am told "the package is of bad quality" but I provide permission.

Did the installation of the printer through the CUPS interface in my browser. Somehow managed to see the proper printer in the Model list. But when I attempt to "Add Printer" I'm prompted repeatedly for username and password and I am providing them (and I am the admin) but nothing beyond this repeating dialog.

---

### Post by rumplestilts on 2016-04-05
Rebooted and went back to the CUPS page. Managed to add the printer using the proper driver that, miraculously, appeared in the list. Doesn't work. Not even the status screen lighting up.

Rebooted. Back into the CUPS page. Added the printer again. This time the driver showed up in the list. Added. Tried printing a test page through the CUPS page. Doesn't work.

Tried adding the printer through the System preferences. Same issue. Just doesn't work. (The driver shows up in the list, however.)

Maybe it really is "of bad quality".

My Android phone prints to the Brother without an issue. My PCs and Macs print without an issue. So is it that Brother makes bad drivers or maybe they just don't care? Or is Ubuntu not doing its due diligence regarding bringing printer manufacturers on board? It took Apple a while to realize this.

Barry

---

### Post by QIII on 2016-04-05
Linux is not Windows, nor is it Apple.  What happens with drivers for other OSes has no bearing on what OEMs provide for Linux.

What power has Canonical?  Canonical, with its meager cash flow and 500 employees, is not in charge of Linux.  Do you expect Canonical to twist Brother's arm to bring them on board?

Its product, Ubuntu, is only one of many distros.

---

### Post by him610 on 2016-04-05
> which one of the names might that be?

My printer is a Brother MFC-7360n; for its name I used "MFC7360N".

---

### Post by rumplestilts on 2016-04-05
Went through this another 50 times with every permutation I could imagine. Nothing.

By the way: I don't expect twisting of arms; rather, I'd expect that Canonical might craft the appropriate *packaging* of the driver so all Brother would have to do is drop the PPD into place and the Driver Installer would do the heavy lifting.

Apple almost went out of business due to (among other things) changing their printing architecture on a monthly basis before finally settling on CUPS (which they bought and then made open-source). It became easy for printer manufacturers to then craft their drivers to work with CUPS. You'd think this would work easily in Linux as CUPS seems to be part of the standard installation; but there's something not quite right so, while it may be nice to ask "why should Ubuntu do this?", it's better to ask, "why -not- do this so those users who want to adopt Ubuntu can do so without printing difficulties?"

I do thank those who tried to help but Ubuntu has lost a customer simply because they choose to not provide the appropriate tools to Brother. Brother has about 15% of the global printer market so it's not like they're the smallest printer company around.

I remember a time when Lotus123 users had to -buy- printer drivers and the developers would only make drivers for certain Epson, HP, and Panasonic dot-matrix printers. I feel like I've been thrown back into 1983 when I try to take a lovely Ubuntu installation and (fail to) make it work in a production environment.

I've been trying to like Ubuntu since v5(?) in 2005 or so but the *same issues keep cropping up.* I won't complain any more. :-({|= :D

---

### Post by ian-weisser on 2016-04-05
> **rumplestilts said:**
> I'd expect that Canonical might craft the appropriate *packaging* of the driver so all Brother would have to do is drop the PPD into place and the Driver Installer would do the heavy lifting.

Brother packages do more than simply installed a PPD.
The ones I used (before I switched to a different vendor) installed proprietary binaries, too.

If Canonical tried to distribute those, they could be succesfully sued by Brother in many jurisdictions.
Brother has not granted Canonical (or anyone else) a license to distribute it's proprietary Linux software.

I think it's stupid...but Brother's stupidity, not Canonical's.

---

### Post by rumplestilts on 2016-04-06
Maybe Apple pays HP, Epson, Brother, etc.? They use something called "AirPrint" which detects the printer and creates a driver for it. Granted, it's not a full-blown set of drivers (I know my Brother printer will only print using AirPrint and not scan so I use Brother's CUPS driver) but it does let almost all modern printer provide some sort of printing services to OSX.

I'll agree that Brother is being stupid about this. Certainly if I decided to throw my lot in with Ubuntu I'd first determine what printers are supported right out of the box.

But I said I was through complaining :D so it is what it is and I won't pound sand.

Thanks,
Barry

---

### Post by QIII on 2016-04-06
What tools did Canonical not provide to Brother?

Ubuntu is open source.  Canonical's packaging process is well known.  It is used by thousands of maintainers of PPAs and others.  It's consistent with the rest of the Debian family.

What is NOT provided is the internal design of the proprietary binary driver from Brother.

We are certainly willing to help you with a legitimate problem to the extent we are able.  But let's be clear about what is happening here and avoid attacking Canonical -- for this.

---

### Post by davidvandoren on 2016-04-06
Open terminal and type

```
sudo ufw allow 631
```


Upper right corner of your desktop click, Systems Settings

Then click printers.

Right click your installed printer and checkmark enabled.

If it doesn't have the checkmark then that was the problem.

---

