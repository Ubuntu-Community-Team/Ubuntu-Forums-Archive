---
title: "PDA: which one ..."
date: 2007-03-30
forum: Hardware &amp; Laptops
---

### Post by neocortex on 2007-03-30
Hello!
There are few very informative threads about pda recommendations. For example:
[http://www.ubuntuforums.org/showthread.php?t=377458](http://www.ubuntuforums.org/showthread.php?t=377458)
[http://www.ubuntuforums.org/showthread.php?t=299021](http://www.ubuntuforums.org/showthread.php?t=299021)
[http://www.ubuntuforums.org/showthread.php?t=274169](http://www.ubuntuforums.org/showthread.php?t=274169)
In summary: either Palm or Nokia 770, according to replies. However, I wonder if Nokia 770 has Office capabilities included (reading Word and Excel documents). It could be excellent solution, being Linux native. Also, Palm Tungstein, T|X and Treo are popular, but is there any comparative test which of the three is the easiest to synchronize with Ubuntu?
I have HP IPAQ 1940 and I can sync it, both via USB and Bluetooth. There are, from time to time, minor slips in syncing tasks and problems with the format of address book entries. Now, I am looking into something new, Linux friendly :) 

Best,
Petar

---

### Post by flaviusc on 2007-03-30
Unfortunate I haven't seen any such comparison so I can't help you there.

I have a Palm Tungsten E2 myself and it works pretty well with Edgy. From time to time it does exhibit some strange problems but it's very usable. The only thing that I miss on the E2 is a WLAN card.

If you want something really Linux friendly then the Nokia 770 or even better the newer 800 is the way to go. That device is running Linux and it has a very nice community at [maemo.org]("http://maemo.org/"). With it the problem of synchronizing a PDA and a PC turns into synchronizing two Linux PCs. Not to mention the incredible application support, just have a look at  the [Application Catalog]("http://maemo.org/maemowiki/ApplicationCatalog2006").

---

### Post by stokedfish on 2007-03-30
I love my Palm TX!

I don't sync anything though, on windows neither...so I can't tell you if it works on linux but prolly yes.

Anyway I just set up an FTP server on my ubuntu and use a client app on my palm to transfer files right to my sd card...works like a charme. And rescobackup backs up all my files every night at 3 am automagically, another reason why I don't sync anything.

So I'd recommend any Palm that supports WLAN with vsftp (or any other FTP server) and rescobackup!  ;)

---

### Post by flaviusc on 2007-03-30
For a list of PDAs and people's experience with them you can have a look on the Ubuntu wiki at [PDADeviceList]("https://wiki.ubuntu.com/PDADeviceList?highlight=%28CategoryPDA%29").

---

### Post by huck416 on 2007-03-31
Hi, see you are syncing to a Palm Tungsten E2. Hoping you can help. I'm very new to Linux but making my way. Having a real issue getting to sync with Palm Tungsten E via USB. Tried several options found in forums but no luck. 

dmesg spits out:

[17180901.332000] visor 6-1:1.0: device disconnected
[17180953.924000] ohci_hcd 0000:05:00.1: wakeup
[17180954.308000] usb 6-1: new full speed USB device using ohci_hcd and address 3
[17180954.524000] usb 6-1: configuration #1 chosen from 1 choice
[17180954.528000] visor 6-1:1.0: Handspring Visor / Palm OS converter detected
[17180954.528000] usb 6-1: Handspring Visor / Palm OS converter now attached to ttyUSB0
[17180954.528000] usb 6-1: Handspring Visor / Palm OS converter now attached to ttyUSB1
[17181024.060000] usb 6-1: USB disconnect, address 3
[17181024.060000] visor ttyUSB0: Handspring Visor / Palm OS converter now disconnected from ttyUSB0
[17181024.060000] visor ttyUSB1: Handspring Visor / Palm OS converter now disconnected from ttyUSB1
[17181024.060000] visor 6-1:1.0: device disconnected

This is repeated several times with some variation in the lef hand column of numbers.
Gnome-pilot is installed and have tried all the options with no success. Usually the Palm will hang requiring a soft reset. I've tried it with Evolution running and not running.
I've tried creating a 10-udev.rules file as descibed here [http://gentoo-wiki.com/HOWTO_USB_sync_for_Palm_PDAs_with_Evolution_2.0_and_udev](http://gentoo-wiki.com/HOWTO_USB_sync_for_Palm_PDAs_with_Evolution_2.0_and_udev) with no success.

In my System Services, udev is not running and am unable to start it ( * Starting kernel event manager...fail!), and that's in Administrator mode. 

I have pilot-xfer installed although haven't exactly figured out how it's supposed to work. Other USB devices work fine.

Ready for any help. Thanks.

---

### Post by neocortex on 2007-04-07
What about SHARP Zaurus? They are not easy to find in Europe, but they seem nice things? Are Nokia 770 and 800 phones too? Can I make a plain, regular call?

Best,
Petar

---

