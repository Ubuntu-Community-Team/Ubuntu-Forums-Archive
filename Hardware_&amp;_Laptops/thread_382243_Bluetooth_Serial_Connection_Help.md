---
title: "Bluetooth Serial Connection Help"
date: 2007-03-11
forum: Hardware &amp; Laptops
---

### Post by michaeljustman on 2007-03-11
I need some help with connecting to my LG VX8300 with bluetooth and making a serial connection.

I can see my phone when I type "hcitool scan" at the command line and I can do a "hcitool cc [phone's MAC]" and I can't tell if I'm connecting to my phone, but I can do "sdptool browse [phone's MAC]" and it list the phone's services.

I know that my dongle is working correctly, but I guess I just need some software with a gui that will allow me to do bluetooth device and service discovery and connect to the phone, so I can point BitPim at a COM port, so I can transfer data back and forth between my phone.

I can't find any info anywhere else. Unfortunately my phone doesn't support bluetooth file transfers... from what I've read that's a breeze with Ubuntu, so I've got to use BitPim.

It works on Windows, but I hate to boot into a proprietary OS to run an open source application. 

Thanks in advance for the answers.

---

### Post by electrofox on 2008-01-04
Hey, I was in need of the same functionality. Except, for my Samsung SCH-u420. The problem was, that I couldn't get the serial connection with the Widcomm software, and Bluesoleil doesn't support my dongle (Kensington, with Broadcom chipset).

The following worked great for me:
[http://ubuntology.com/2007/10/27/access-your-phone-via-bluetooth-with-ubuntu-gutsy/](http://ubuntology.com/2007/10/27/access-your-phone-via-bluetooth-with-ubuntu-gutsy/)

Hope that helps. (Feel free to let me know if it does.)
-ElectroFox

[COLOR="#EEEEEE"]Samsung
SCH-U420    U420
Bluetooth     Kensington
Dongle         Broadcom
Widcomm     Bluesoleil
Linux           Ubuntu
BitPim         Bit Pim
Serial          Connection
File Transfer[/COLOR]

---

### Post by electrofox on 2008-01-17
Hmm... Well, it's been a couple weeks, and now I had needed to connect my phone again, but forgot what commands to issue once I paired it with my computer.  So, I went to this post to find out how I did it before.  Unfortunately, I didn't really tell how to do it, but only posted a link to the place that I found out how to do it.  This wouldn't have necessarily been a problem, except that the site seems to be down now.  I looked at some of the commands that were in my terminal history, though and found out how again. Here are those commands:
```

**hcitool scan** *<-look for the mac address of your phone*
**sdptool browse XX:XX:XX:XX:XX:XX** *<-look for the channel for the Serial Port Service*
**rfcomm connect 0 XX:XX:XX:XX:XX:XX #** *<-replace # with the channel you found.*

```
Mine was channel 4, so it would be:
```

**rfcomm connect 0 XX:XX:XX:XX:XX:XX 4**

```
Substitute your phone's mac address for the X's in all of the commands.
This is all assuming that you have already paired your phone with your computer, first.
After the last command is issued, the terminal should reply:
```
Connected /dev/rfcomm0 to XX:XX:XX:XX:XX:XX on channel 4
Press CTRL-C for hangup
```
Now you can use BitPim to access your phone (select rfcomm0).
(Note: DO NOT press Ctrl+c until you're done with BitPim or whatever other reason you were connecting  to serial.)

That's all there is to it!  Hope that helps.
-ElectroFox

---

### Post by seanf on 2008-02-09
electrofox - i noticed you said you have a u420... I've followed these instructions, and I'm able to connect to the /dev/rfcomm0

BitPim doesn't have u420 in the supported phone list, so I've selected "other cdma"... BitPim then can detect the phone, but can't d0 anything with it other than that.

How are you able to use BitPim with the u420?

---

