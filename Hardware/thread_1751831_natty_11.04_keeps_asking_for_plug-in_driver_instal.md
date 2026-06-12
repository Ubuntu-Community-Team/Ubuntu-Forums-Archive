---
title: "natty 11.04 keeps asking for plug-in driver installation hp 1018"
date: 2011-05-07
forum: Hardware
---

### Post by stijnblommerde on 2011-05-07
os: ubuntu 11.04 natty
printer: laserjet 1018, usb connected to laptop

problem: natty keeps asking for plug-in driver installation

problem description: each time i startup my laptop or each time i plug in the usb cable of the printer the following procedure starts: hp printer driver plug-in installation > download > plug-in installation succesful. the printer works after downloading and installing the plug-in, but why do i need to keep installing the driver over and over again?

did not have this problem in 10.10 or 10.04.

thanks, stijn

---

### Post by asadmalik on 2011-05-09
I am having the same issue with my laserjet 1018. The printer fails to print the document even after the re-installation of driver/plugin, which i have done every time i connected my printer to my pc.

never faced such a problem on 10.10 .

the hplip version installed is 3.11.1
Please anyone?

---

### Post by Askari on 2011-05-10
I am having the self same problem with my HP LaserJet 1018. I have to download the plug-in every morning,then the printer works fine for the rest of the day.

There must surely be a cure for this, but can anyone tell me what it is?

---

### Post by meijer.o on 2011-05-15
I have this (HP 1018 laser jet) printer and the same problem, i have no idea how to debug this. Can somebody help?

Best regards, Otto

---

### Post by stijnblommerde on 2011-05-17
1. terminal: sudo apt-get remove hp*
2. system settings - hardware - printer - delete hp printer (if installed)
3. restart your computer (maybe not necessary, but i did)
4. system settings - hardware - printer - add printer
5. terminal: sudo hp-plugin

update: i have to repeat step 5, each time i start my computer.

---

### Post by meijer.o on 2011-05-18
The only thing that worked for my was installing the foo2zjs package from the lucid repository,

Otto

---

### Post by stijnblommerde on 2011-05-24
> **meijer.o said:**
> The only thing that worked for my was installing the foo2zjs package from the lucid repository,

Otto
hi meijer.o, 

i would like to try your solution. following questions arise: within ubuntu natty 11.04: how to add the lucid repository? how to add the package foo2zjs?

thanks, s

---

### Post by sm_ashiq on 2011-05-26
I am also having same problem on HP Laserjet 1018 Printer, please provide us a solution asap.

---

### Post by Nannygoat on 2011-05-29
Same thing here, LaserJet 1018. Here's a solution I found at the Russian forum. I'll give it a try tomorrow at the office:

```
sudo getweb 1018
sudo hplj1018
```

---

### Post by theindustry on 2011-05-30
Also had this problem for some time now: [https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/780983](https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/780983)

Tried the above fixes but no change. Running [FONT=Courier New]sudo hplj1018[/FONT] throws an error, so I am guessing that I'm stuck with the default hplip-drivers.

---

### Post by floritaka on 2011-06-03
I tried to solve this by installing the new HPLIP drivers (hplip 3.11.5) from [http://hplipopensource.com/hplip-web/install_wizard/index.html](http://hplipopensource.com/hplip-web/install_wizard/index.html) 

The driver have a control panel and some tools, it didn't solved the problem entirely but at least a download is no longer necessary. However this printer requires that the firmware gets uploaded to the printer everytime its turned on, and this panel doesn't do it automaticaly so in order to function correctly, every time the printer is turned on that should be  done manually through the option: Download Driver, in the panel of HP.

---

### Post by Askari on 2011-07-05
Having decided to live with the fact that I had to download the plug-in every morning, a few days ago the problem stopped. I am no longer asked for the plug-in, and my HP LaserJet 1018 prints as normal.

I can only think that the problem was rectified in one of the routine updates.

---

### Post by dungeonmasterShu on 2011-09-27
I have also been having problems with the HP LaserJet 1018 Printer, altho mine are slightly different (on xubuntu)...

First when i plug in or reboot with the printer connected it starts a plug-in install window, when i try download and install i get an error - plug-in file does not match its digital signature... file may have been corrupted or altered... Error Code 2.

I have since installed HPLIP and the toolbox detects the printer and shows it is working fine, however (altho it goes through the motions on the laptop) nothing actually prints, ie. the printer does nothing.

When i unplug (USB) and plug in (or reboot) i get a similar dialogue to the one before HILIP but this one is clearly from within HPLIP, and i get the same error...

I have tried various suggestions found in these forums (remove and reinstall, install through term, etc) but nothing seems to help.

the installer has an option to use an already downloaded file to install from rather than downloading via the program, i have searched google and hp for a download file for this printer for linux and i just end up (literally) going round in circles, hp sends me to another site and that sends me back to hp... and the HIPLIP site is not very helpful.

i have been using (x)ubuntu for less than a week and linux (mandriva) for about 3 years, but have only worked in KDE, and know VERY little of term commands.

if anyone is able to help, will much appreciate it!

---

### Post by arkanabar on 2011-10-04
I'm still having this problem.  I tried installing hplip, wouldn't print.  Removed hplip, wouldn't print.  ran sudo hp-setup, command not found (cos it's part of hplip).  running hp-setup, I get this output:
```
Downloading plug-in from: http://www.openprinting.org/download/printdriver/auxfiles/HP/plugins/hplip-3.11.1-plugin.run
Downloading plug-in: [******************************************************] 100%  8.0 KB   Receiving digital keys: /usr/bin/gpg --no-permission-warning --keyserver pgp.mit.edu --recv-keys 0xA59047B9
 
error: Plug-in file does not match its digital signature. File may have been corrupted or altered. Error code: 2
```[LIST=1]
[/LIST]

---

### Post by wbari on 2011-10-14
Hi, I have Ubuntu 11.04 installed recently. I have HP Laser jet P1007. But I am not able to install it. Every time it is connected I get the message for Plug in installation. However, when I opt for its download, the following message is there
"error:  ERROR: Plug-in file does not match its digital signature.  File may have been corrupted or altered.  Error code: 2 "
Can anybody help.
Waseem

---

### Post by john bengston on 2011-10-24
I had the same problem on a HP lasterJet P1006 and I sent problem to ubuntu and I received this reply from them:
                                          
[Sanjay Kumar (sanjay-kumar14)]("https://launchpad.net/%7Esanjay-kumar14")          said     on 2011-09-18:      #1   
    Hi,
 Plugins for HPLIP are uploaded at [http://www.openprinting.org]("http://www.openprinting.org/")  website, which is unfortunately down due to an unexpected issue. Since  the webserver is not available, installation of plugins is failing. We  will get back to you once we make alternative arrangements for accessing  the plugins.
 Thanks,
Sanjay Kumar

         It seems that hackers have hacked into the website for hp drivers and they are down because of that.
It is the only website that you can download HP drivers from.....so the solution is to use another printer or use windows instead....I think Bill Gates is behind it somehow. I am sure he hates Ubuntu in lesssening his take home pay.

I love ubuntu and I tell everybody about it all the time but to have this problem with HP printers is a bummer.Just be patient and everything will work out all right after they get the problem fixed.We'll just have to use windows or another printer in the mean time...I always have another printer around that i can plug in and use besides HP.


john

---

### Post by arkanabar on 2011-11-07
well, it looks like openprinting.org is back up.  So I'm going to give this a new shot.

---

