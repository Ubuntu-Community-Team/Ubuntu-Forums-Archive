---
title: "HP Laserjet P1006 Printer, not Working on Ubuntu"
date: 2010-07-04
forum: Hardware
---

### Post by madmax.santana on 2010-07-04
I am trying to install my printer in Ubuntu. It says it has to download a third-party plugin but when I click next, it says there is some problem with my network connection. My network connection is absolutely alright and so is my Printer. It works on Windows...
Please help.
Few days back I install OpenSuSE and I managed to set up my printer after a lot of problems. Is printing from Linux that difficult.
[Here]("http://forums.opensuse.org/english/get-help-here/hardware/440577-hp-laserjet-p1006-printer-not-working-device-comm-error.html") is OpenSuSE forums problem discussion thread.
But I don't think this solution will work with Ubuntu. Kindly help me, I am in desperate need! Thank you!

---

### Post by madmax.santana on 2010-07-04
Ok. I have downloaded and install hplip and even the blue hp icon is visible in my panel...
But the printer doesn't print.

---

### Post by madmax.santana on 2010-07-04
Oh come on fellas!!!
Does that mean this printer is useless for Ubuntu???

---

### Post by dino99 on 2010-07-04
a quick search on google will give you lot of posts about this printer, such as:

[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9323540](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9323540)

[https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)

---

### Post by madmax.santana on 2010-07-05
The second link was not that useful. Been there. Done it all. No help.
The first one was helping. But I swear I googled like hell but couldn't find this thread. Now, could you please tell me how to restart my cups???

EDIT:
It worked... Thanks a lot... I had been going crazy over it for two days... Thanks a lot dino99... You owe me one... :)

For anyone else who come looking for help:

- Uninstall cups, hpijs and hplip... Rather purge them. Like this
> $sudo apt-get remove --purge hpijs hplip cups
Then reinstall them
> $ sudo apt-get install hpijs hplip cups
Then run hp-setup as root...
IMPORTANT, do [COLOR="Red"]NOT[/COLOR] 
> $ sudo hp-setup 
Rather log in as root and then run hp-setup
> $ su -
$ Password:
$ hp-setup
The setup will continue and all will be well in a minute or so.
Thanks to all who helped... :) Marked SOLVED.

---

