---
title: "How do I set up dial-up under Ubuntu....?"
date: 2009-07-24
forum: Hardware
---

### Post by jrickert on 2009-07-24
I put another post up earlier but maybe I wasn't very specific.  I have just added 9.04 to my laptop along side of XP.  It boots and runs fine.  I just can't see how to get my dial-up connection set up.  Any help would be fine.  If I can get this working, I probably will never have to boot up XP.

Thanks, John

---

### Post by wojox on 2009-07-24
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

---

### Post by Gaming4JC on 2009-07-24
Unlike the previous post, which links to an infamous wiki wich knows nothing, I can say from experience it is a pain to setup Dial-Up on the current 9.04 and with each release it seems to get harder since they don't feel anyone uses it anymore. :(

On the contrary, many people (including myself) use Dial-Up. That being said, you will need to find several things.

First of all, if your modem is not a Conexant modem, it is a "Winmodem", back in the golden age these were supported by patched linux kernals and the like. But now there is no support what so ever. If you have a Conexant you can purchase the driver via Linuxant. If not, like most people... <_<

You will need to purchase what they call a hardware modem. This can either be a modem which connects via a COM1 serial port or a USB port. I can say for a fact that the TrendMicro's external serial modem works great.

Once you have selected a good modem, and purchased it at a reasonable price, you still cannot just plug it in and expect it to work by itself. Since you have no way of getting Ubuntu's "dependencies" without being online, the only way to do this is to download it off-line and via a portable USB drive/thumbdrive take the files to your laptop and install them. To save you the effort of tracking down all the dependencies you will need, I have packaged together a tar.lzma which contains the debs to get you started. See my blog post for more info:
[http://g4jc.net84.net/wordpress/?p=198](http://g4jc.net84.net/wordpress/?p=198)

Once you install the dependencies you should be able to type:
```
sudo gnome-ppp
```

Into a terminal and then enter the needed information about your modem and your ISPs account information. If all goes well you can dial-up perfectly and save your settings. :)

---

### Post by jrickert on 2009-07-24
So let me understand this.  I have a panasonic laptop, Satellite A105-s3484 and XP sets up my connection with little or no effort.  I assume this is the Conexant you are talking about.  If I further understand you, I have to purchase a driver from Linuxant.

How can I tell if I have a Winmodem or this Conexant you talk about?

Sorry to be so stupid about this but communications is not one of my specialties.  I don't think I need an external modem as XP seems to do it internally.

Thanks, John

---

### Post by Gaming4JC on 2009-07-25
Well, sadly Windows XP detects a lot more things by default than does Ubuntu when it comes to modems.

Concerning whether or not yours is a Conexant you can check via the tools listed on the linuxant site:
[http://www.linuxant.com/drivers/modemident.php](http://www.linuxant.com/drivers/modemident.php)

Either use ScanModem on Ubuntu or simply use List Modem on Windows XP as mentioned. Both tools are fairly geeky in terms that they bring up either Command prompt or Terminal, lol.

Once you get the output please post it here. You can use quick-edit in the Windows Command prompt to copy the window, or simply right click copy in Ubuntu Terminal.

I have a sad suspicion it is not a Conexant, as these type of wonderful modems are only found on about 5 out of 10 ppls computers. My eMachines had one, but my Compaq did not, lol...

Anyway let me know your results. :)

---

