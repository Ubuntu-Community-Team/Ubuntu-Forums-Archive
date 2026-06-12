---
title: "USB to Serial converter, set-up in wine"
date: 2008-07-16
forum: General Help
---

### Post by jonlemur on 2008-07-16
I've got a USB to serial adapter that I need to get configured to work with some Windows software that's running in wine.  The software requires a selection of COM1-COM4, and I can't just put in /dev/ttyUSB0.  By doing ```
cd ~/.wine/dosdevices
ln -s /dev/ttyUSB0 ./com4 
``` I was able to get the software to recognize the port and receive data from the device that's connected to it.  The data is a bit choppy though--it doesn't receive data as well as it does when I'm just running the software in Windows (with all the same hardware).  

I don't know much about this kind of thing, but I thought that I might be able to improve the data transfer by making it low-latency.  I found a program, setserial, that I would be able to do this to ttyS0-S4, but it won't work on ttyUSB0.  I've searched quite a bit but haven't been able to find a way to do this.  Any suggestions?

---

### Post by jonlemur on 2008-07-17
bump

---

### Post by jonlemur on 2008-07-17
Well, it works now.  I don't know if I just had to restart the computer, or what the deal was, but it works perfectly :)

---

### Post by lemboy4 on 2009-04-16
jonlemur, you are amazing.  I had to get a USB-over-serial program working for programming and ARM chip, and your command worked first try.  Thanks.

---

### Post by michaelayland on 2009-10-13
Thank you for this information. Having connected a serial out Davis Weather Monitor II weather station to their weatherlink software by way of a Keyspan 19 converter it of course failed! but with you kind two lines of commands it runs like clockwork.. Thank you very much
Best Regards and the Barometric Pressure is 1030mbars
mike a

---

### Post by chicorasia on 2009-11-04
I was having issues with Onset HOBOware, until I stumbled into this:

[http://wiki.jswindle.com/index.php/Wine_Registry#Serial_Com_Port](http://wiki.jswindle.com/index.php/Wine_Registry#Serial_Com_Port)

Adding registry entries for serial ports worked like a charm.

good luck

---

### Post by petermckinley on 2010-09-17
I just had to sign up to this forum to thank jonlemur, id been trying for 2 hours to get my prolific usb-serial converter (pl-2303) to talk to a Lectrosonics mixer using their Lecnet Master Pro software in Wine, sheer bloodymindedness since it works perfectly in XP on my dual boot lappy!. Just when my head was thoroughly pickled i stumbled upon his reply, pasted the code in a terminal and voila!! it worked immediately, no reboot required. Awesome..must be some kind of voodoo

---

### Post by mlloyd on 2010-10-13
> **petermckinley said:**
> I just had to sign up to this forum to thank jonlemur, id been trying for 2 hours to get my prolific usb-serial converter (pl-2303) to talk to a Lectrosonics mixer using their Lecnet Master Pro software in Wine, sheer bloodymindedness since it works perfectly in XP on my dual boot lappy!. Just when my head was thoroughly pickled i stumbled upon his reply, pasted the code in a terminal and voila!! it worked immediately, no reboot required. Awesome..must be some kind of voodoo

It worked for me too, and was very easy to do. I'm using the same USB-serial converter as you, to access an old CPU-XA home automation (X10) interface. I already had the software in wine.

---

