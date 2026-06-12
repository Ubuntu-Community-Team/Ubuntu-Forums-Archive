---
title: "Why are printers so difficult to set up on Ubuntu? (Need help with Brother printer)"
date: 2021-12-11
forum: Hardware
---

### Post by lowang2 on 2021-12-11
I have Ubuntu 21.10 installed and can't get my Brother MFC-7860DW recognized/connect to print over my network. 

I've downloaded and installed the drivers from the Brother website using the terminal but was unable to print a test page. 

In the Printer Properties I'm getting the following message: Processing - Unable to locate printer "*printer_IP_address*".

I'm pretty sure I have the printer URI address set up correctly (it's just the "printer ip address" right? I put "ipp://*_printer_IP_address*/ipp/print" (this didn't work either))

The "ping" command in terminal give me the following: "ping: *printer_IP_address*: Name or service not known"

How do I fix this and get the printer to work over the network?

---

### Post by yancek on 2021-12-12
The link below explains setting up a network Brother printer which might help.

[https://kbpdfstudio.qoppa.com/install-printer-driver-on-linux/](https://kbpdfstudio.qoppa.com/install-printer-driver-on-linux/)

If you can't ping the printer you will not be able to print from that printer so you need to resolve that first.  I don't use network printers so can't help any more.

---

### Post by mIk3_08 on 2021-12-12
> **lowang2 said:**
> I have Ubuntu 21.10 installed and can't get my Brother MFC-7860DW recognized/connect to print over my network. 
I've downloaded and installed the drivers from the Brother website using the terminal but was unable to print a test page. 
In the Printer Properties I'm getting the following message: Processing - Unable to locate printer "*printer_IP_address*".
I'm pretty sure I have the printer URI address set up correctly (it's just the "printer ip address" right? I put "ipp://*_printer_IP_address*/ipp/print" (this didn't work either))
The "ping" command in terminal give me the following: "ping: *printer_IP_address*: Name or service not known"
How do I fix this and get the printer to work over the network?
I do have Brother Printer/Scanner installed in my Linux Ubuntu Operating System and its working smoothly so far and its connected via WiFi. And the scanner too working with Xsane Image Scanning Apps. 
And I run this for a few years now without any hassle. Thanks to Linux Ubuntu Dev.
Here is my screenshot below;
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289639&stc=1[/IMG]

---

### Post by foggybrain on 2021-12-12
I am running Ubuntu 20.04, no problems with my two Brother printers (MFC-J4610DW & MFC-J4540DW), the 2nd one my default. Both connect great via WiFi, however, I found it very useful to install the default printer driver tool (which includes scanner files) MFC-J4540DW downloading driver files from Brother website, this had the advantage of making the scanning facility much more stable.  Download and install procedures from Brother site are simple to follow.  See link to UK site (change for your location).............[https://www.brother.co.uk/support/drivers](https://www.brother.co.uk/support/drivers)

---

### Post by kurt18947 on 2021-12-12
I guess the method I use to connect Brother printers could be viewed as archaic but it does work reliably. I assign static I.P. addresses to each printer. I've installed system-config-printer which I feel gives me more control. Right-click the desired printer, enter the sudo password if requested then properties. In the 'Device URI' I enter

```
socket://xxx.xxx.xxx.xxx
``` where x= i.p. address. 

My newest Brother printer - MFC-J4535DW - does work with driverless printing and scanning but I prefer the Brother supplied drivers.

Edit: 13 December For anyone going to the Brother web site, many of the directions seem outdated with Ubuntu. Most of the steps are not required; they may have been required in the days of 8.04 but no longer.

---

### Post by The Cog on 2021-12-12
> The "ping" command in terminal give me the following: "ping: printer_IP_address: Name or service not known"
That sounds as though it doesn't recognise printer_IP_address as an IP address, and it is trying to do a name to IP lookup.
Please copy and paste both the ping command and the resulting output so we can check what's going wrong there.

---

### Post by ajgreeny on 2021-12-12
If you go into your router setup page there will probably be a tab which allows you to reserve IP addresses for devices, which is how I usually set up my wireless printers, admittedly HP in my case, but that shouldn't make any difference.
Once you have the IP address reserved try pinging it; if you can then manage a ping it should make the wireless connection easier, even though I do not know Brother printers so I am not sure of the procedures needed to get them working.

---

### Post by him610 on 2021-12-12
The Brother instructions to install a MFC device are pretty straight forward. My non-wireless MFC-7360N is connected to the local network with a Cat-5 cable, so I can not give advice on a wireless connection; however, the one absolute necessary step is to go into the printer Network Configuration utility to assign it a stable IP address. You do not want to have wandering IP addresses every time your router gets rebooted.

---

### Post by mIk3_08 on 2021-12-13
Here also the screenshot of my detected brother scanner on my Linux  Ubuntu Operating System. It run successfully with Xsane imaging  application program without any hassle. It runs smoothly and perfect  match to my hardware machine.
I get to show you this to prove to you that I  do have same brand of your hardware and it runs smoothly to Linux  Ubuntu Operating System. This also works via WIFI connection. 
Good Luck and Cheers.

[https://ubuntuforums.org/attachment.php?attachmentid=289640&stc=1](https://ubuntuforums.org/attachment.php?attachmentid=289640&stc=1)

---

### Post by SeijiSensei on 2021-12-13
Dump the wifi and connect the printer directly to your router with an Ethernet cable. Give it a static IP address outside the range of addresses managed by the router's DHCP server. I have a HL-3170CDW connected this way, and all my devices can see it.

---

