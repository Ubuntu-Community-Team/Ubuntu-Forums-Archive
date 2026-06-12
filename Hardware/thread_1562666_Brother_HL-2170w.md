---
title: "Brother HL-2170w"
date: 2010-08-27
forum: Hardware
---

### Post by J-Morris on 2010-08-27
I just bought a Brother HL-2170w. I followed the directions [here]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html#dpkg3") and consulted the posts [here]("http://ubuntuforums.org/showthread.php?t=897227") and [here]("http://www.openprinting.org/printer/Brother/Brother-HL-2170W") and [here]("http://ubuntuforums.org/showthread.php?t=1533869&highlight=2170w") and [here]("http://ubuntuforums.org/showthread.php?t=590793&highlight=2170w") and [here]("http://ubuntuforums.org/showthread.php?t=590793&highlight=2170w") and so on to no avail. 

I have the printer connected via USB, it appears in CUPS:

```
Description:	HL2170W
Location:	
Driver:	Brother HL2170W for CUPS (grayscale)
Connection:	usb:/dev/usb/lp0
Defaults:	job-sheets=none, none media=iso_a4_210x297mm 
```

but nothing ever ever ever prints. Sometimes, a notification pops up that says the printer may be disconnected. 

I do not have access to Windows or macOS, I do not want to use it as a wireless printer. 

Here is the print server error log:
```
E [27/Aug/2010:20:29:33 -0400] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"!
E [27/Aug/2010:20:40:29 -0400] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"!
E [27/Aug/2010:20:55:03 -0400] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [27/Aug/2010:21:03:03 -0400] Returning IPP client-error-bad-request for Create-Job (ipp://localhost:631/printers/HL2170W) from localhost
E [27/Aug/2010:21:03:19 -0400] Returning IPP client-error-bad-request for Create-Job (ipp://localhost:631/printers/HL2170W) from localhost
E [27/Aug/2010:21:04:33 -0400] Syntax error on line 12 of printers.conf.
E [27/Aug/2010:21:04:33 -0400] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [27/Aug/2010:21:08:56 -0400] [CGI] Unable to get PPD file /printers/HL2170W.ppd: 404 - Not Found
E [27/Aug/2010:21:08:57 -0400] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"!
E [27/Aug/2010:21:09:45 -0400] [CGI] Unable to get PPD file /printers/HL2170W.ppd: 404 - Not Found
E [27/Aug/2010:21:09:45 -0400] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"!
E [27/Aug/2010:21:19:27 -0400] Returning IPP client-error-document-format-not-supported for Print-Job (ipp://localhost/printers/HL2170W) from localhost
E [27/Aug/2010:21:27:54 -0400] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [27/Aug/2010:21:29:04 -0400] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"!
E [27/Aug/2010:21:36:12 -0400] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"!
E [27/Aug/2010:21:39:44 -0400] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"!
E [27/Aug/2010:21:41:47 -0400] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"!
E [27/Aug/2010:21:49:02 -0400] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [27/Aug/2010:21:49:04 -0400] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [27/Aug/2010:22:03:00 -0400] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [27/Aug/2010:22:03:01 -0400] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [27/Aug/2010:22:03:31 -0400] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [27/Aug/2010:22:03:32 -0400] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [27/Aug/2010:22:06:17 -0400] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [27/Aug/2010:22:06:19 -0400] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [27/Aug/2010:22:24:12 -0400] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [27/Aug/2010:22:24:13 -0400] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [27/Aug/2010:22:33:13 -0400] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [27/Aug/2010:22:33:14 -0400] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory

```

So

a)Hoe can I make it work? To me, this seems unlikely at this point even though the printer is known to be a working printer. 

b)If for whatever reason Brother HL-2170w will not in Ubuntu 10.04, how/who do I notify to change the various wikis and lists indicating that this printer is compatible with linux (anymore)?

---

### Post by Fir3chi3f on 2010-08-28
Did you try the regular Ubuntu printer setup? Its under System>Administration>Printing

I looked there myself and did see the printer listed.

edit: Oops! didn't realize this was kubuntu, should be a similar process however.

---

### Post by cycling-rod on 2010-08-28
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)
Is the above link any help?
Using Ubuntu Lucid:
I have a Brother laser printer HL-2030 which wasn't on the printer driver's list, so instead I used the driver for HL-1050 and it worked. This may help you to find an alternative driver. Good luck!

---

### Post by J-Morris on 2010-08-28
Thanks for the replies. I tried setting up the printer through the KDE4 control center, also through CUPS and printconf, so no avail. Trying different drivers was a good idea and I tried a few other drivers I'd heard of other people using that worked, including the 1240 and 2030, but none of them worked. 

This is a very well regarded printer, so it's sad that it doesn't work, and internet research seems to indicate that it stopped working specifically in 10.04, so whatever, Ubuntu always seems to be taking two steps forward and one step back for every new edition, which (obviously) I can live with*. 

I can't find any evidence at all of anyone getting these printers working across USB, so it seems, if you want to use a Brother with Linux, you have to configure it to be wireless with a Windows box, which is not an option for me.

---

### Post by J-Morris on 2010-08-28
Well, I solved the problem by returning the Brother to Staples and buying an HP Laserjet pro P1606. I installed it through CUPS and it worked right away, and it has duplexing.

---

### Post by Maximus_ARNP on 2010-11-28
Following method has worked every time I have tried. Here is how to setup the wireless:

This instruction is to setup Brother Laser printer 2170W in LinuxMint, Ubuntu or Windows 7.

**Part 1: To reset the printer & establish a wireless connection between a Printer & a router**
[INDENT]Turn off the printer.
**Press and hold the Go Button** in front, at the same time turn on the printer from the right side. You will see three lights (Error, Drum, Toner) turn on. Release the Go button. The light is not blue and is off.
Now, **Press the Go button 7 times.** Wait for some seconds.
The three lights will turn on and off by themselves. The printer warms up and then stops.
**Connect the ethernet cable **to the wireless router and the printer
In the browser type: [http://192.168.2.1](http://192.168.2.1) **[[Or your router's IP address]]**
**Confirm** that your printer is on network listed in the DHCP client list.
Now, in your internet browser type in IP ADDRESS of your PRINTER.
**Network configuration** --- **Configure wireless** Make sure **Communication Mode** is Infrastructure
**Wireless Network Name (SSID)** -----**Browse**------**Select your Wireless Network.**
**Channel** is same as **your network's channel number**.
**Authentization Method** should be WPA/WPA2-PSK (or **the authentication method of your network**)
**Encryption method** Choose same Encryption as **your network's encryption method.**
**Network Key** <do not change anything>
**Passphrase** : <Enter your network passphrase>
**User ID and Password:** <Leave them blank>
**Submit.**
Now wait until you get instruction in the browser: **&#8220;If the Ethernet cable is connected to this machine, please remove it.&#8221;**
**Disconnect** your Network cable from the Printer.
Your Printer will print two pages. 2nd page will describe Wireless settings. **Confirm** that the setup is successful.

[/INDENT]
**Part 2: Configuring Printer to have a STATIC IP address (So, you do not have to add a printer in  UBUNTU---SYSTEM---ADMINISTRATION---PRINTING every time you restart your router or printer):**

[INDENT]In your web browser open [http://192.168.2.1](http://192.168.2.1) (or **your router's IP address**)
Find the list of DHCP clients. (You will find your Printer's NEW IP address here.)
In your web browser **open Your Printer's NEW IP address** while it is connected wirelessly. For me it is [http://192.168.2.5](http://192.168.2.5)

**Network Settings** ---- **User: admin Password: access **---- **Configure TCP/IP **---- **IP Address: ** 192.168.2.199  (Note that last 3 number should be kept on higher side, so it does not conflict with your Network's DHCP fuctions. Most likely it is not going to be a problem.)
And, **BOOT METHOD : STATIC.** [[If you leave this DHCP, your printer's IP address will change at every reboot of your printer, requiring UBUNTU to DETECT & ADD the printer at every restart of the printer.]]
[/INDENT]
[B]Part-3: Defining the Printer's NODE NAME to more human-readable name:
[/B]
[INDENT]In your browser, **go your printer's IP address**.
**Log in.**
**Network Configuration ---- Wireless ----  click on Node Name.**
**Update Node Name** to [COLOR="Red"]**Brother-HL2170-wireless**[/COLOR] (up to your preference).

**Network Configuration ---- Wired ----  click on Node Name.**
Update Node Name to [COLOR="Red"]**Brother-HL2170-wired**[/COLOR] (up to your preference).
**RESTART YOUR PRINTER.**
**SUBMIT.**
[/INDENT]
**Part-4: Add Printer in UBUNTU System**
[INDENT][B]Ubuntu ----- START ----- SYSTEM ---- ADMINISTRATION ---- PRINTING.
ADD --- PRINTER ---- NETWORK PRINTER ---- [/B]Wait 30 seconds for the system to detect the printer automatically. If printer is not found automatically, type in IP address of the printer and probe for it. 
**Select Your Printer. Selecting [COLOR="Red"][B]JETDIRECT (PRINTER'S IP ADDRESS)**[/COLOR] works for me.[/B]
**FORWARD**
You may change the name of the printer if you wish.
**APPLY.**
[B]Print TEST PAGE.
DONE.[/INDENT]
[/B]
ENJOY.:popcorn::-({|=

Credit mainly to:  "Difficult to setup the wireless connection" on June 24, 2010 by zionlionboy on Cnet.com

---

### Post by bestbatteryshops on 2010-11-29
This is a very well regarded printer, so it's sad that it doesn't work, and internet research seems to indicate that it stopped working specifically in 10.04, so whatever, Ubuntu always seems to be taking two steps forward and one step back for every new edition, which (obviously) I can live with it .:p

---

### Post by headcount on 2011-01-08
Just want to thank Maximus_ARNP for the step-by-step instructions.  I just moved over from Windows, and I'm printing with no problems on Ubuntu 10.10 64-bit.  Some parts that were important for me:

- When first logged into the router (192.168.1.1), set up a static IP address.  The last three digits should be high, like in the 140's.  

- Now when in the Brother web interface, go to Network -> Configure TCP/IP, choose static and enter in the IP address, subnet mask, and gateway (same as the router IP)

- After that step, I had to re-connect to the wireless via the web interface.  No problem.

- Disconnect, and Ubuntu will find the printer!  And the static IP is set if you need to update the wireless info at any point in the future.

Thanks again!  I think this Linux thing will catch on...

---

### Post by koebes on 2011-01-17
Hi,

I use ubuntu 10.10 and manage to install my 2170W via ethernet or wireless (thanks to the description above) 

BUT: I can't print the testpage. It says there is an error sending the page to the printer. A troubleshooter comes up and says printer is not activated. But when I activate it, the error message comes up again and deactivates the printer automatically.

Only thing I can find is that it cannot read the toner level. Could there be some problems with my AMD64 bit version?

No ubuntu guru so please give me step by step instructions if you need specific informations on my system/configuration :D

Thanks a lot,

Nils

---

### Post by goodbye-windows(tm) on 2011-08-09
I have a Dell laptop and the Brother 2170W printer with Xubunbtu 11.04 installed. It had been running under windoze, so the printer and the wireless was already set up.

The printer>router connection is wireless. The computer>router connection is hardwired.

So, the majority of my setup was already done.

I checked items 1, 2, and 3 as listed in the message above from Maximus. All looked ok. I downloaded both linux drivers and placed them on my desktop and proceeded with step #4. The test page looks like a million bucks, although I haven't tried printing a file from the word processor yet.

I was (literally and seriously) done in 5 minutes (after spending 3 hours reading the forums posts and downloading the drivers).

Thanks so much to Maximus and to the forums administrator(s). I'm now one step closer to dumping windows completely.

Regards,

Art

---

### Post by ieee488 on 2012-12-18
Post by Maximus_ARNP works beautifully for Ubuntu 12.04 with wired connection.

With 12.04 I did not have to install any drivers.

---

