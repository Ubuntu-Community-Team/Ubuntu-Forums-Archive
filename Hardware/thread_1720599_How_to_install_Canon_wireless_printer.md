---
title: "How to install Canon wireless printer"
date: 2011-04-03
forum: Hardware
---

### Post by emilward on 2011-04-03
I can't seem to be able to figure out how to install my canon MX340 series wireless printer. When I plug it in via USB Ubuntu 10.10 automatically installs it with no problem at all. But I want to install it wireless so I don't have to be plugged in. Can anyone help? I downloaded the drivers from canon but I'm not even sure what to do with these.

---

### Post by ProNux on 2011-04-03
I checked the Canon (USA) website and I found no Linux drivers.  You mean you downloaded the Windows driver?  I'm not sure if you can use ndiswrapper with this one.

---

### Post by walt.smith1960 on 2011-04-03
People seem to have better luck with Canon downloading from Canon's Asian or European web sites.  If the printer installed, I wonder if you just need to change the device URI and possibly change something on the printer.  When I install one of my Brother printers, the install process installs a USB connection even though there's not a USB cable connected.  Try opening printing and right-click on the printer icon.  Click on "properties" and see what the device URI says.  My messed up Brother install starts out usb:/ something.  I just change that to socket://xxx.xxx.xxx.xxx:9100 where the x's are the I.P. address and I'm golden.  You'll want to assign a static I.P. address to the printer if you use this procedure because you're specifying an address.  Again, this is Brother not Canon but there may be similarities.  Windows drivers won't work anyway anyhow as far as I know.  Good luck, people seem to have decent luck with Canon.

---

### Post by emilward on 2011-04-03
Okay here's how I got my Canon Pixma MX340 printer installed:

first I plugged it in via USB. Ubuntu 10.10 detected it and installed it, no problem, right away. Next I went to System>Administration>Printing 

In the "Printing-localhost" window I saw my printer, "MX340 Series". From here I clicked on Add which brought up the 'New Printer' window.

Under the 'Devices' list (on the left side) I clicked on 'Find Network Printer'. Now on the right side I saw a field to enter in the 'Host'. (From here I printed out the LAN setting from my printer) I typed in the IP address of my printer and then click on 'Find'.

After giving it a few seconds my printer was shown. I clicked to add my printer and it was now shown right next to my printer I added originally except with a different icon.

Next I plugged in the USB cable and Ubuntu found my printer again. From here I deleted the printer from the 'Printing-localhost' window that I originally added. Next I right-hand clicked on my printer (that I just added again) and click on 'enable' in the down menu. Both "enable" and "share" at this point are now clicked. 

And thats it. Its now working wireless. I don't know if this is the "correct" way or if I just got lucky but either way. This is what worked for me. Thanks for everyones help. I hope this helps out other people who have this same problem with this printer.

---

### Post by walt.smith1960 on 2011-04-03
> **emilward said:**
> Okay here's how I got my Canon Pixma MX340 printer installed:

<snip>
And thats it. Its now working wireless. I don't know if this is the "correct" way or if I just got lucky but either way. This is what worked for me. Thanks for everyones help. I hope this helps out other people who have this same problem with this printer.

Congratulations! I don't have sharing enabled but I don't know of a downside to it being enabled.

---

