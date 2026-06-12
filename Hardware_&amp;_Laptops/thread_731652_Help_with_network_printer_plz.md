---
title: "Help with network printer plz"
date: 2008-03-22
forum: Hardware &amp; Laptops
---

### Post by angelusx on 2008-03-22
Hello, 

sorry for dumb question but im fairly new to linux of any kind...

i have a Canon MX850 AIO connected to my network via ethernet port on the printer.  I have 3 desktops and 2 laptops running windows xp and 1 laptop and 1 desktop running ubuntu 7.10

On the windows systems i simply install the driver for the printer and create a network port for the printers ip address in order to print.  I can not seem to find the equivelant in ubuntu... every option seems to want a port or server with no way to simply enter the ip of the printer.  I also wasnt able to find a driver to match exactly but figured one of the other canon drivers may work if i can just get the ip configured properly.  I downloaded something called turboprint which seemed a bit easier than the Administration > Printing setup but still it wanted ports and servers.  

Any help would be greatly appreciated... TIA all

also... all of the web pages and forum posts i have found with screen shots do not match what i see when adding a printer.

---

### Post by reyhan on 2008-03-22
what is your printer model?

---

### Post by reyhan on 2008-03-22
Do you install samba file server on your ubuntu?

---

### Post by karhulitos on 2008-03-22
Hmm..

I have a Samsung CLP-300N and I never did anything else but inserted IPP Printer (Printer URI: ipp://192.168.0.133 in my case) port and I've been printing ever since.

Works on my machine -certified..

---

### Post by angelusx on 2008-03-22
Thanks for the responses guys...

ok so, the printer prints with no problems when connected via USB but i still can not get anything to print from the network.

i have tried ipp and lpd addresses of 

ipp://192.168.0.50 and lpd://192.168.0.50 but get no response from the printer.

i have also tried adding /ipp to the end of the string as in the example when adding a printer but nothing seems to work.


any help would be appreciated guys

TIA

---

### Post by angelusx on 2008-03-24
admitting defeat...

gave up and went back to windows :( lol

---

### Post by oldsoundguy on 2008-03-24
too bad, when most likely all you had to do was make the printer available to the network via cups.

---

### Post by angelusx on 2008-03-24
ubuntu would not communicate with the printer at all unless it was connect via usb.  the printer is connected via ethernet to the network.

---

### Post by Growinold on 2008-03-27
I was having all sorts of trouble with this also until I found this guide. It's not exactly the same system, but the steps are similar enough that I was able to follow and get mine running.

I hope it works for you: [http://www.growinold.com/storage/howto_network-usb-printer_suse-9.2.pdf]("http://www.growinold.com/storage/howto_network-usb-printer_suse-9.2.pdf")

---

### Post by angelusx on 2008-03-29
thanks for the resonse Growinold,

i actually tried that and several other procedures i found on the web, actually spent a good 5-6 hours messing around with it... found couple others that could not get this same printer to print over ethernet, so im not sure what the issue is :(

thanks again tho ^^

---

