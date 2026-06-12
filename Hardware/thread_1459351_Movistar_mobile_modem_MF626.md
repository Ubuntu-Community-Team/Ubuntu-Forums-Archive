---
title: "Movistar mobile modem MF626"
date: 2010-04-21
forum: Hardware
---

### Post by calvimm on 2010-04-21
Hello.

I am in Guatemala and just bought a mobile prepaid broadband modem from Movistar; MF626 HSDPA.

using karmic.

So far I've set it up (using a hyperterminal in Windows XP) for plug and play using the info from here: [[http://ubuntuforums.org/showthread.php?t=1359410&highlight=modem+mf626]](http://ubuntuforums.org/showthread.php?t=1359410&highlight=modem+mf626])  and that worked.

Then i tried this: [http://ubuntuforums.org/showthread.php?t=1147685](http://ubuntuforums.org/showthread.php?t=1147685)

Which didnt do anything. I need to know how to set up the modem and how to work the prepaid aspect of it all.

mostly. i just want internet. help!

thanks

---

### Post by glonk on 2010-04-23
The link you are using points to a thread that uses a version of Ubuntu prior to Karmic. The network manager is the way to go with this device in Karmic. 

If you are referring to the _ZTE_ MF-626, this 7 month old thread explains how to do it:
[http://ubuntuforums.org/showthread.php?t=1302235](http://ubuntuforums.org/showthread.php?t=1302235)

I used the Ubuntu-only method. Had problems with the suggested .gtktermrc file. The configuration causes gtkterm to fail to read any of the .gtktermrc file and therefore will not communicating with the correct port. Exchange this line: 
> term_background_saturation    =** 0,500000 **
With:
> term_background_saturation    = **500000                      **I also used this setting:
> port    = /dev/ttyUSB**2**
Look in the Configuration menu of gtkterm and select 'local echo' so you can see what you are typing.

Once I had turned off the auto-run mode on the device, I unplugged, re-plugged and clicked on the network manager. Click new connection and you should see a list of ISP providers.

Because I own a Telstra network device, I selected the 'telstra default' choice when prompted. And it all works perfectly. Your mileage may very.

So just to clarify:
I have a **ZTE MF-626** Usb Modem connected to **Telstra BigPond on ** **pre-paid in Australia**. 

The device is configured properly and it** connects / disconnects / reconnects superbly in Ubuntu 9.10 ****[B]Karmic Koala**.[/B]

:)

---

### Post by calvimm on 2010-04-25
i have it set up to plug and play mode no problem.

my main question is how do i go about setting up the new connection. IE. what information do i need to gather? i have the APN and the DNS, user name and password, the pin i expect is from my SIM card? after the *99# i put my movistar phone number, correct? i use all this info and try to connect but it still wont connect.

---

### Post by calvimm on 2010-04-27
SO.

i got it to work. and it connects. and most of the time it works. however, as of right now i keep getting the ugly "server not found" when i go on firefox. however, my skype connects and my torrents continue to download...

any suggestions?

---

