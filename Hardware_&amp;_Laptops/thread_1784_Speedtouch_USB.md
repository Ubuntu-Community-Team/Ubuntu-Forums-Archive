---
title: "Speedtouch USB"
date: 2004-10-22
forum: Hardware &amp; Laptops
---

### Post by Pedro on 2004-10-22
Hi,

I'm new here so a big "Hi" to everyone.
I'm now downloading the first release of Ubuntu, but I'm using the PR version right now. I can't connect to the internet using my modem: Alcatel/Thompson Speedtouch USB ("the green fish"). The modem is detected but, like almost all the distros around, it's very hard to use it. I know I need the microcode but yesterday I checked the modem site @ [www.speedtouchdsl.com/produsb.htm](www.speedtouchdsl.com/produsb.htm) and I saw that Thompson released the driver source code!
I'm not an expert, but i think that with the source code, it can be easy to make the modem work.
Is someone having the same problem? Can anyone help?

Thanks in advance.

---

### Post by judas_iscariote on 2004-10-22
take a deep look on

[http://linux-usb.sourceforge.net/SpeedTouch/](http://linux-usb.sourceforge.net/SpeedTouch/)

---

### Post by judas_iscariote on 2004-10-22
or try this:

$sudo modprobe CDCEther 


and tell me..what happend...

---

