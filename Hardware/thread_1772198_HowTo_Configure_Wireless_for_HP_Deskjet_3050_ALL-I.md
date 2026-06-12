---
title: "HowTo: Configure Wireless for HP Deskjet 3050 ALL-IN-ONE J610a on Ubuntu 10.04"
date: 2011-05-31
forum: Hardware
---

### Post by jerremy-tamlin on 2011-05-31
HowTo: Configure Wireless for HP Deskjet 3050 ALL-IN-ONE J610a on Ubuntu 10.04

[INDENT]*[COLOR="DarkRed"]Following this howto requires you to disconnect from the Internet/HomeNetwork for a short time. A pdf version containing **screenshots** is attached to the bottom of this post.[/COLOR]*[/INDENT]

[LIST=1]
[*]Turn on the printer and press the wireless button
* Select “Setting” &#8594;  “Enable Wireless” on the printer's console
* The Blue Light will begin flashing.

[*]Right Click on the Network Manager Icon and select “Edit Connections...”
* Select “Auto HPJ610a.0513DC” (*or similar*) and click “Edit”
* Under the “IPv4” tab choose “Link-Local Only” from the “Method:” drop down list.
* Click “Apply”
* Click “Close”

[*]Select the “HPJ610a.0513DC” (*or similar*) wireless network from the Network Manager

[*]Click the Wireless button on the printer again and choose “Settings” &#8594;  “Defaults” &#8594;  “OK”
* Click “Enable Wireless”
* “Not Connected” should change to “Connecting...”
[*]Click “Print Reports”
* Your Printer should print a couple of pages.
* On the first page under the section “General Information” take note of the “URL(s) for Embedded Web Server” mine was [http://169.254.19.220](http://169.254.19.220)
* Enter this address into a web browser
[INDENT][I]Note: I have fiddled around with this and it appears that the “Connecting...” will not change to “IP: 169.254.19.220” until after you have opened that address in a web browser.
If your printer has timed out and gone back to “Not Connected” before you get a browser open just press the wireless button again and select “Settings” &#8594;  “Disable Wireless” then “Settings” &#8594;  “Enable Wireless” again.[/I][/INDENT]

[*]Once you have a web browser open and are looking at the “Deskjet 3050 All-in-One J610a Embedded Web Server” Select the “Network” tab and click on “Wireless Setup Wizard”

[*]Follow the Wizard to select your network and enter your networks password.
Note: When you click finish you will loose your connection to the page and wizard.

[*]Press the wireless button and take note of what the ip address has changed to. Mine is “IP: 10.1.1.11”

[*]Connect to your home network again and enter this new ip address (10.1.1.11) into a browser.
* You should be able to access the “Deskjet 3050 All-in-One J610a Embedded Web Server” once more.

[*]Start the “HP Device Manager” by opening a terminal and typing “hp-setup” (Alternatively you could press ALT+F2 and enter “hp-setup” there.)
* Choose “Network/Ethernet/Wireless network (direct connection or JetDirect)” and Click “Show Advanced Options” and check “Manual Discovery”
* Enter the printer's IP Address (10.1.1.11) and click “Next”
* You printer should be found. Click “Next”
* Optional: Enter a description/location and check “Send test page to printer” if you want.
* Click “Add Printer” to finish
[/LIST]

Thanks heaps to Donald Broatch and Francesca Terenziani for their comments here [https://answers.launchpad.net/hplip/+question/135694](https://answers.launchpad.net/hplip/+question/135694) which gave me the info I needed to write this HowTo. :-)

Jesse Williamson
[www.windwanderer.com.au](www.windwanderer.com.au)

---

### Post by Cfossy2 on 2011-06-08
I followed this tutorial closely, I had initially had problems starting the installation, due to wrongly named folder. I then tried to set up the printer according to the tutorial, but did not use the manual discovery. Then I used the manual discovery, and hey presto, the printer was discovered, and I printed wirelessly, using Ubuntu 10.04. thanks for putting up this tutorial, great work.:p

---

### Post by jerremy-tamlin on 2011-06-23
Hay thanks for the feedback. Getting feedback like yours makes it worth the time spent to document. Cheers :D

---

### Post by AmbroseOh on 2011-07-21
This doesn't seem to work for me. I tried manual setup and entered IP but it doesn't detect my printer. Keep getting the error message "error: No devices found on bus: net". Thanks for the help.

**EDIT**: It seems I had to download a new version of hplip. Everything seems to working now. Thanks!

---

### Post by cforput on 2011-08-12
> **AmbroseOh said:**
> This doesn't seem to work for me. I tried manual setup and entered IP but it doesn't detect my printer. Keep getting the error message "error: No devices found on bus: net". Thanks for the help.

**EDIT**: It seems I had to download a new version of hplip. Everything seems to working now. Thanks!

AmbroseOh,
what version of hilip did you use? I just downloaded the latest version and I get the same problem, my printer isn't detected at all. I used hilip-3.11.7

Also, I am trying to get this printer working on my Ubuntu 11.04 AFTER I set it up on 3 Windows laptops (XP, Vista and W7). Not sure if that matters or not.

---

### Post by DrPotoroo on 2011-08-30
I am also using Ubuntu 11.04 and getting the same "error: No devices found on bus: net" after using the manual discovery. Can anyone help?
 
**Edit: **The printer had been showing a successful connection to my wireless network and displaying an IP address. However, it wasn't showing up in my router's list of attached devices. Ater turning the printer off and on again, the printer couldn't connect to the wireless network at all. So I reset the printer to defaults and followed the OP's instructions again. Then it all worked fine.

---

### Post by Bushcraft Bill on 2011-09-21
I get it to print perfect when in my browser [Embedded Web Server] but not with any other programs?

When I do an admin test print from printing localhost I get this - idle-/usr/lib/cups/backend/hp failed 

so why does it work on way and not the other?

---

### Post by ivesjd on 2011-11-25
Just want to add that I was getting a "Internal System Error"

Seems to be an issue with the Security Certificate. Was seeing it a lot more in Google Chrome than in Firefox. Just refresh the page.
Hope this helps someone.

---

### Post by henrythemouse on 2012-08-18
2012-08-18
This HowTo saved me a lot of headaches!

Thanks a bunch, I was beginning to think I would never get the wireless to work on this printer under Linux. All I did was follow your steps and it worked. I used it on Ununtu 12.04.

I can't thank you enough.

---

### Post by geronl on 2012-09-12
> **jerremy-tamlin said:**
> HowTo: Configure Wireless for HP Deskjet 3050 ALL-IN-ONE J610a on Ubuntu 10.04* 
Right Click on the Network Manager Icon and select “Edit Connections...”


In Ubuntu 12.04 the Network doesn't have "Network Manager" or "Edit Connections"

Is there any further update on the new Ubuntu version?

---

