---
title: "Buggy wireless on dell inspiron b130"
date: 2006-10-07
forum: Hardware &amp; Laptops
---

### Post by colonelmac on 2006-10-07
Hey,
I installed Ununtu on my dell inspiron b130. Ubuntu recongized the wifi card out of the box. But the card didnt work. I checked this site and it said that the drivers were supported by Ubuntu but the firmware wasnt. So I got the firmware working. I was able to get the wireless card to scan and pick up other wifi networks. Then when I choose a network to connect to and press OK, it takes a long time then never really connects. And I get stuck on that wireless network. I have to reboot to get it off that one. ](*,) 

please help me. 
Thanks.

---

### Post by SqdnGuns on 2006-10-07
What are the specs for your WiFi card?

---

### Post by colonelmac on 2006-10-07
Dell Wireless 1470 Dual Band WLAN MiniPCI card. (Broadcom)

---

### Post by Frogger on 2006-10-07
I have the same laptop, and my wifi card works.

Start by blacklisting the braodcom driver that comes with Ubuntu, the driver is not compatable with the firmware aon your card (as you stated):

Do this by opening a terminal and typing

sudo gedit /etc/modprode.d/blacklist

and adding the line 

blacklist bcm43xx

Then install ndiswrapper:
In a teminal type 

sudo apt-get install ndiswrapper

Then go to the ndiswrapper wiki list and get the driver for your card
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

or copy bcmwl5.inf and bcmwl5.sys from your original windows partition

Then go to the directory where you stored the inf and sys files and type 

ndiswrapper -i bcmw15.inf

Then type 

ndiswrapper -l
 
To make sure it worked, if it did not, just uninstall the driver (with ndiswrapper -e bcmw15) and reinstall. (I have sometimes had it not work the first time)

Last reboot

Just wondering, what did you do to get the firmware to detect a network?

---

### Post by Frogger on 2006-10-07
Sorry for the ugly format I forgot what the tag was to get the code box.

---

### Post by dolphinsonar on 2006-10-08
I had a similar problem.  I installed "Wifi-radar" using synaptic package manager and now the computer just hops on the strongest signal automagically.  It only hiccups if it needs a wireless key.

Managing the wireless through the installed "connection properties" setting is a little clunky if you take your laptop to different places often (which is why you should have a laptop).

Hope it works!

---

