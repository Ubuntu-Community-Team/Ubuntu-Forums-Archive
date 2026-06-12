---
title: "Speedtouch USB Modem"
date: 2005-02-18
forum: Hardware &amp; Laptops
---

### Post by Arrondor on 2005-02-18
I know this issue has been covered in a number of places but I still cannot get my Thomson Speedtouch USB Ver4 modem to work under Ubuntu. (wanting to connect to wanadoo in the UK)

So far I have tried the instructions posted in the how to section of this website and also [http://linux-usb.sourceforge.net/SpeedTouch/ubuntu/warty.html](http://linux-usb.sourceforge.net/SpeedTouch/ubuntu/warty.html)

I abandoned SUSE 9.2 as I could not get the modem or my soundcard to work.  The sound works fine in Ubuntu but not the modem.

I love the ubuntu experience but the lack of an internet connection is turning me away from linux and back to the dreaded Windows XP.

Please Help!!

---

### Post by Jad on 2005-02-18
I have same modem, I'm not sure about Version4, I have SpeedTouch 510
and btw I'm with Wanadoo Jordan. 
now you will have to set up your eth card 
IP address: 10.0.0.1
subnet  255.255.255.0
gateway 10.0.0.138
when done, activate it, then with your browser go to [http://10.0.0.138/](http://10.0.0.138/)
go to advance -> easy setup and setup your Internet connection from there. 
from now on, it will be always on connection.

---

### Post by MrFunster on 2005-02-20
I think Arrondor is referring to the speedtouch 330 USB modem, rather than what sounds like a router/modem combined to me (not sure, but you referred to setting up a NIC so I'd assume it has no direct USB connection)

I'm in the same boat as far as the Speedtouch 330 goes, having triedto set it up variously with Knoppix, debian Suse live.

I got instructions from [Here](http://www.ubuntulinux.org/wiki/UKSpeedtouchDSLHowTo) 

but it refers to installing the package **speedtouch**  from the universe repository, and I'm not sure how to access this (if it's on the web I can't access it owing to the fact that my modem isn't configured!).

Sorry if I'm hijacking this thread, but any help for me may also help Arrondor.


edit: after a little bit of trawling the forums (something I should have done first -I'm an old hand on other forums), I found a link to universe, and the package can be downloaded and burnt to disk or whatever [Here](http://archive.ubuntu.com/ubuntu/pool/universe/s/speedtouch/) 

HTH

---

### Post by Arrondor on 2005-02-21
Thanks for you help MrFunster, but I need a little bit more please...

When accessing your second link (re Universe), which file should I download?

Secondly, when I have saved ito floppy etc what do I need to do with it?

I presume you have successfully got your speedtouch 330 working with these instructions?

Sorry about the need for the additional help but I am so new to Linux I am not sure how to do anything much.  I am still working on how to create directories etc!

---

### Post by poofyhairguy on 2005-02-21
[QUOTE=Arrondor]Thanks for you help MrFunster, but I need a little bit more please...

When accessing your second link (re Universe), which file should I download?[/QUOTE]

this one I bet:

[http://archive.ubuntu.com/ubuntu/pool/universe/s/speedtouch/speedtouch_1.3.1-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/s/speedtouch/speedtouch_1.3.1-1_i386.deb)

[QUOTE=Arrondor]Secondly, when I have saved ito floppy etc what do I need to do with it?[/QUOTE]

Go to the disks menu. Copy the file into your home folder (/home/yourname/). Open the terminal. type:

sudo dpkg -i  speedtouch_1.3.1-1_i386.deb

follow the rest of the instructions.

---

### Post by MrFunster on 2005-02-22
[QUOTE=Arrondor]Thanks for you help MrFunster, but I need a little bit more please...

When accessing your second link (re Universe), which file should I download?

Secondly, when I have saved ito floppy etc what do I need to do with it?

I presume you have successfully got your speedtouch 330 working with these instructions?

Sorry about the need for the additional help but I am so new to Linux I am not sure how to do anything much.  I am still working on how to create directories etc![/QUOTE]


I haven't got it working yet, just pointing you in the right sorta direction, and hoping someone can help both of us (which appears to have happened ^^^)

To be honest I haven't got much time to play around after I finish work, so I am stuck using Windoze most of the time, I have a caddy which has my Linux install on and one with XP/98, making transferring files a bit of a pain.
As soon as I get it working I'll let you know.

---

### Post by MrFunster on 2005-02-26
UPDATE

I failed to get the userland driver working, so I decided to have a go with the kernel drivers.

After a lot of faffing around I got it working, but I did have problems.
When I printed the web page out, it did not tally with the actual web page:[http://linux-usb.sourceforge.net/SpeedTouch](http://linux-usb.sourceforge.net/SpeedTouch)

 (the perils of working in windows I reckon)
In the end I saved the page as raw textand copied the appropriate text.
When I rebooted - presto hey! I have a DSL connection- this post being testament to it

All I neddo now is find a driver for my printer and I'm ready to rock and roll

---

