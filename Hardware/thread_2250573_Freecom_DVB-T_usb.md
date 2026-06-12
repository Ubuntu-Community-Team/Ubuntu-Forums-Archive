---
title: "Freecom DVB-T usb"
date: 2014-10-29
forum: Hardware
---

### Post by ian60 on 2014-10-29
Hi, I'm a total newcomer to Lynux and I have no idea what to do with my DVB TV usb stick to get it to work.
It's a Freecom25451rev3, I did ask at Freecom and they emailed me this:

[SIZE=3]wget [http://home.arcor.de/efocht/dvb-usb-wt220u-fc03.fw](http://home.arcor.de/efocht/dvb-usb-wt220u-fc03.fw)  
(ok I have the firmware from another source as this just took me to Yahoo, but now seems to work now I have written it here)

sudo cp dvb-usb-wt220u-fc03.fw /lib/firmware
(but what the hell am I supposed to do with this?)

Then they say plug my usb tv reciver in. 


AGGH!! Why can't people speak English any more? 


[/SIZE]

---

### Post by Thee on 2014-10-29
That's a command that will copy a file called "dvb-usb-wt220u-fc03.fw" in a folder named "/lib/firmware/" on your computer.

To use this command, you need to open a program called "Terminal" and paste (or type in) your command there. Then press enter and type in your password in order to give it permission to copy that file there.
(Bare in mind that when entering your password you wont see it on screen, but its there)

See attached screenshot to get a clue of what that should look like.

[ATTACH=CONFIG]257589[/ATTACH]

---

### Post by ian60 on 2014-10-29
Thank you for your help.
One step closer now.  

It says no such file or directory.

Where do I put the file to be copied? On the desktop? Root directory?

---

### Post by Thee on 2014-10-29
Put it in your home folder, or just edit the command to point where your file is located, like so:

sudo cp **/path/to/the/file/**dvb-usb-wt220u-fc03.fw /lib/firmware

---

### Post by ian60 on 2014-10-29
Sorted, thank you for your help. :)

---

### Post by Thee on 2014-10-29
No problem, glad to be of use ;)

---

