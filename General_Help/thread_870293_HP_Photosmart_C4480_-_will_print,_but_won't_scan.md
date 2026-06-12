---
title: "HP Photosmart C4480 - will print, but won't scan"
date: 2008-07-25
forum: General Help
---

### Post by GrantB on 2008-07-25
Hi,

I recently got a HP Photosmart C4480.  Printing is fine -- all I did was connect the USB and OpenOffice found it and printed just fine.

I can't figure out how to use the scanner, though.  When I start up XSane, it says "No devices available".

I tried installing HPLIP Toolbox, but this can't seem to find my printer either.  "hp-info" finds "No devices found", which is odd, as clearly OO has no problem finding it.  Also, after installing HPLIP, strangely the only new programs in my menu are two fax-related programs.  I expected something more....

This page [http://hplip.sourceforge.net/supported_devices/index.html]("http://hplip.sourceforge.net/supported_devices/index.html") suggests that HPLIP doesn't support this printer (yet?).

Can anyone offer a suggestion to help get my scanner in action?  Thanks.

By the way, I'm on 7.10 Gutsy Gibbon.  I've been putting off upgrading...

---

### Post by hansdown on 2008-07-25
Hi GrantB. I have the c4210 and all I need to do is place a document in the scanner and the display on the printer machine lets me scan from there. Is yours the same?

---

### Post by coffeecat on 2008-07-25
[This page]("http://www.sane-project.org/sane-mfgs.html#Z-HEWLETT-PACKARD") doesn't list your actual model, but shows that several Photosmart scanners are not supported.

Which is very frustrating because HP is one of the better manufacturers for Linux support.

Is there any chance of your being able to change that machine? I've got a HP Officejet 6310 All-in-One and everything works fine ootb. And despite the name, it prints photoquality (with the correct inks) very well.

Apart from [http://www.sane-project.org](http://www.sane-project.org) , the other site you might want to bookmark (and you might find it useful to check out the printer half of your machine) is [http://www.linuxfoundation.org/en/OpenPrinting](http://www.linuxfoundation.org/en/OpenPrinting)

---

### Post by GrantB on 2008-07-25
hansdown,
Do you mean "Scan to PC", where you control the scan from the printer control?  I tried that, but it didn't work: "Scan Error.  Try scan from computer or see documentation."

coffeecat,
Do you mean to try a different PC?  Sorry, I only have the one Linux machine.  (I guess I could try my wife's Windows machine, but that won't really help diagnose anything.)

---

### Post by phidia on 2008-07-25
> sudo apt-get install hplip-gui That will install an interface in System>Preferences.

---

### Post by hansdown on 2008-07-25
GrantB, sorry to be so vague. What I mean't was, the small screen at the front left of the scanning cover. There should be three buttons; scan, print, and copy. These are functional, but the actions don't show on your computer screen.

---

### Post by coffeecat on 2008-07-26
> **GrantB said:**
> coffeecat, Do you mean to try a different PC?

Apologies for not being clear. I meant, could you exchange the printer/scanner for another one? Depending on consumer rights in your country you may be able to. For instance, here in the UK, if you buy from a distance seller (delivered to the door) you have a right in consumer law to return it for refund/replacement within (I think) 30 days - no questions asked. If you buy from a high-street retailer, your rights are more restricted but some of the big retailers can be quite generous. Good for public relations, I suppose.

On the other hand, some retailers can be downright awkward. :(

---

### Post by Sef on 2008-07-26
> 

HP Photosmart c4400 series

Supported by HPLIP (requires HPLIP version 2.8.5 or later).

Distro	Version	Installer	GUI	Scan	

Ubuntu	5.04	No	        Yes     Yes		
Ubuntu	5.1	No	        Yes	Yes		
Ubuntu	6.06	Yes	        Yes	Yes
Ubuntu	6.10	Yes	        Yes	Yes	
Ubuntu	7.04	Yes	        Yes	Yes	
Ubuntu	7.10	Yes	        Yes	Yes		
Ubuntu	8.04	Yes	        Yes	Yes	

What version of HPLIP is installed on Gutsy Gibbon?

---

### Post by GrantB on 2008-07-26
hansdown,
Yeah, I tried initiating the scan from the HP's panel.  As I said earlier, didn't work.  

coffeecat,
Not really an option.  This model was free with purchase of a Mac (purchased for my job).  This is the only model to choose from without added cost.

phidia,
Thanks.  I actually did install the gui, I just didn't look in the right menu for it.  However, "ERROR: No device found or unsupported device."

Sef,
Where'd you get that info from?  It appears my version is 2.7.7, so I guess that's my problem.  Can I use the Ubuntu management tools to upgrade HPLIP without upgrading my whole Ubuntu install, or do I need to use apt-get or something?  (I really am a noob when it comes to system administration, sorry.)

---

### Post by fyo on 2008-07-26
Even Hardy doesn't have that new a HPLIP (2.8.2, FYI).

If you go to the official HPLIP site, you can download an Automatic Installer which claims to work with Ubuntu from 6.06 onwards:

[http://hplip.sourceforge.net/downloads.html](http://hplip.sourceforge.net/downloads.html)

That's probably your best (and easiest) bet.

---

### Post by GrantB on 2008-07-26
fyo,
Thanks!  That was exactly what I needed.  The printer and scanner is up and running perfectly now.

Thanks Sef and fyo!

Sef (or anyone else), if you have a minute, I'd like to know where your quoted text came from.  Thanks.

---

### Post by AliceP on 2008-09-08
I'm new to open source. Using Ubuntu 8.04 Dell 1525n factory install. HP C4480 All-In-One Printer. After much work I figured out what my problem was.
Searched HP for Linux for the C4480 and they sent me to sourceforge page.
Downloaded the automatic installer file  hplip-2.8.7.run file option from [http://hplip.sourceforge.net/downloads.html](http://hplip.sourceforge.net/downloads.html). The file would not run in the terminal as stated in the directions.

Ubuntu 8.04 HELP gave me the solution. Right clicking the downloaded file, Properties -Permissions-Allow executing file as program CHECK Mark...Close.

Now double click on the file, Click on Run In Terminal and it does the rest.

Will restart the system after install in terminal window. You may have to turn the printer off and on and unplug USB until recognized. 
All the software for printing, scanning, and icons are working.
The system sees it as C4400 but that is the HP Series it is in.

Hope this helps someone out there new to Ubuntu 8.04 like me.:)
Alice

---

### Post by suityou01 on 2009-01-20
OMG, I bought an HP Photosmart C4480 as it was listed as a supported device.

I installed HPLIP from Sourceforge (2.8.12) and ran the setup. All was working fine.

Today I come to scan and it is not working.

I have uninstalled HPLIP and reinstalled.

If I do a lsusb I can see it listed on USB 002 DevId 007

In hp-setup it says it cannot find any devices so I did a manual find,using the above 002:007 id. It just says the device is turned off or not communicating.

So gutted. This was all working. I am running gutsy btw.

---

### Post by moz44 on 2009-04-19
I bought Photomart c4480 3 months ago, but I never needed the scanner until now. To make it short, with Synaptic Package Manager, I installed the following packages:
[LIST]
[*]hplip
[*]hpoj
[*]hplip-gui
[/LIST]

at first, i realized that only two menu items were present in App > Office. However, some time later I noticed System > Preferences > HPLIP Toolbox. This is what you need for scanning, printing, etc from the pc. The interface is rather friendly.

hope it helps

---

### Post by Trent T on 2009-05-31
Hi all-- 
Its possible that some of the routine updates for Ubuntu can reset HPLIP to a previous version that does not allow your HP Photosmart 4480 to scan;

I did the same things as the rest of you, and got it to scan by downloading the most recent HPLIP from Sourceforge and installing it from a terminal window (ie., not with synaptic).  It scanned very well for a few months after that.  Then it stopped scanning.  

I found that HPLIP had been reset to a lower version, 1.X.X or something.  

So I downloaded again, and reinstalled the current HPLIP (3.9.4b in May 2009), and it scans again.

--Trent T

My system: Ubuntu 8.0.4 running on a 32-bit generic PC from TigerDirect.

Sourceforge link to the HPLIP Linux driver:

[http://hplipopensource.com/hplip-web/downloads.html](http://hplipopensource.com/hplip-web/downloads.html)

---

### Post by moz44 on 2009-05-31
For those in trouble with the scanner or printer, I advise to remove the configuration files for HPLIP before you install or reinstall HPLIP. The configuration files for HPLIP reside in the hidden folder .hplip in /home/username/
So, delete the folder and then you log out and log in for HPLIP to recreate the default configuration. Please realize that this technique will solve many other issues with most programs.


I hope it helps,

---

### Post by co_mtnbiker on 2009-11-21
This worked for me.  Went to website and followed instructions.  Very easy.  Thanks.

---

