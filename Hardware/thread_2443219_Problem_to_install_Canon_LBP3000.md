---
title: "Problem to install Canon LBP3000"
date: 2020-05-12
forum: Hardware
---

### Post by rodrigom27 on 2020-05-12
Hi everyone!

I'm a new user of GNU/Linux. 
I install Lubuntu 18.04 32-bit (have an old notebook).

I'm having problems to install the printer Canon LBP3000.
I plugged it to the USB and went to "System tools --> Printers" and I can see it there. But it doesn't work. When I send a page, it shows "procesing..." and nothing happens.

I made a search on Google and find many tutorials to install it from the Terminal (that's how I arrived to this forum). But I can not make it work.

Please, I would appreciate your help. If you need further information, please tell me what it is.

Regards!

---

### Post by kurt18947 on 2020-05-12
I recently found a Canon resource. I don't have a Canon printer so I can't say if it works or how well it works. Use at your own risk. I also don't see LBP3000. This site is Canon USA, perhaps you need Canon Europe or something like that. I hope that someone knowledgeable about Canon printers will check in with better advice.

[https://www.usa.canon.com/internet/portal/us/home/support/product-finder/support-printers?cm_sp=CSO-_-PFListing-_-pixma_mgseries#pixma-mgseries](https://www.usa.canon.com/internet/portal/us/home/support/product-finder/support-printers?cm_sp=CSO-_-PFListing-_-pixma_mgseries#pixma-mgseries)

---

### Post by rodrigom27 on 2020-05-12
Thanks kurt18947!

You're right: the only Canon site where I find something for this printer is Canon-Europe. I downloaded the drivers from there, but coudn't install them. It says it can't satisfy the dependencies.

---

### Post by CelticWarrior on 2020-05-13
> **rodrigom27 said:**
> Thanks kurt18947!

You're right: the only Canon site where I find something for this printer is Canon-Europe. I downloaded the drivers from there, but coudn't install them. It says it can't satisfy the dependencies.

So please post the link to the drivers and describe how you tried to install and the error messages.

---

### Post by rodrigom27 on 2020-05-13
> **CelticWarrior said:**
> So please post the link to the drivers and describe how you tried to install and the error messages.

I downloaded different versions from here: [https://www.canon-europe.com/support/consumer_products/products/printers/laser/i-sensys_lbp3000.html?type=drivers&language=en&os=linux](https://www.canon-europe.com/support/consumer_products/products/printers/laser/i-sensys_lbp3000.html?type=drivers&language=en&os=linux)

I followed the instructions they have (readme.txt): first install the "common" .deb file and then the "capt" .deb

But both of them says "dependencies cannot be satisfied". Some versions ask for "cupsys" and "cndrvcups-common" others for "gs-esp" and "cndrvcups-common".

---

### Post by CelticWarrior on 2020-05-13
"CAPT Printer Driver for Linux v2.71" is new enough, should work.

---

### Post by rodrigom27 on 2020-05-14
> **CelticWarrior said:**
> "CAPT Printer Driver for Linux v2.71" is new enough, should work.

Thanks for your response.

I used those, but don't work.

Now I could install them and have no problem with dependencies.

But it doesn't print.

Something curious: If I check the properties, it shows connection is "/dev/usb/lp0" (as I put during the installation, following the driver's instructions). But if I put to change it, it shows it as the current connection, but it also appears "Canon LBP 3000 (0000A1A579DJ)" and if I clic on it, it says "A printer connected to an USB port". 
So, I understand that it detect the printer and I didn't connect it well.

Anyway, when I send a page to print, it shows "Processing". But if I change the connection to that "Canon LBP... etc", and send to print, it says "Processing - Sending data to the printer".

I hope that info can help you to help me.

Thanks!

---

### Post by rodrigom27 on 2020-05-15
Update:

I finally could print one page. 
The status pass from "inactive" to  "processing" and then "inactive" again.

BUT when I send another page to print, it pass to "processing" and nothing happens. After reboot the computer, it printed it without my intervention.

This is a great advance, but I don't want to restart the computer every time I need to send another work to print.

I run the "troubleshooter" and it told me: "No system journal entries were found. This may be because you are not an administrator. To fetch journal entries please run this command: su -c 'journalctl -u cups.service --since="None" --until="2020-05-15 19:29:50"' > troubleshoot-logs.txt"

I did, and this was the response:

"Failed to parse timestamp: None"

Any ideas??

---

### Post by ab1el on 2020-11-03
After some troubles installing a Canon LBP 3000 printer on Ubuntu 18.04 i found this [https://github.com/hieplpvip/ubuntu_canon_printer](https://github.com/hieplpvip/ubuntu_canon_printer)

I used the commands from the Readme, then selected the printer and it worked when i tried to print.
> 
[COLOR=#24292E][FONT=-apple-system]Supported Models[/FONT][/COLOR]
[LIST]
[*]LBP-810
[*]LBP1120
[*]LBP1210
[*]LBP2900
[*]LBP3000
[*]LBP3010
[*]LBP3018
[*]LBP3050
[*]LBP3100
[*]LBP3108
[*]LBP3150
[*]LBP3200
[*]LBP3210
[*]LBP3250
[*]LBP3300
[*]LBP3310
[*]LBP3500
[*]LBP5000
[*]LBP5050
[*]LBP5100
[*]LBP5300
[*]LBP6000
[*]LBP6018
[*]LBP6020
[*]LBP6020B
[*]LBP6200
[*]LBP6300n
[*]LBP6300
[*]LBP6310
[*]LBP7010C
[*]LBP7018C
[*]LBP7200C
[*]LBP7210C
[*]LBP9100C
[*]LBP9200C
[/LIST]

(Before i tried installing using this one [https://tutorialforlinux.com/2019/03/28/printer-canon-i-sensys-lbp3000-lbp3010-ubuntu-driver-how-to-download-install/](https://tutorialforlinux.com/2019/03/28/printer-canon-i-sensys-lbp3000-lbp3010-ubuntu-driver-how-to-download-install/)  but it was not printing)

---

