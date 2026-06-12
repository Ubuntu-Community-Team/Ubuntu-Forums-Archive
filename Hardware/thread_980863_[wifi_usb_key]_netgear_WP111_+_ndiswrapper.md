---
title: "[wifi usb key] netgear WP111 + ndiswrapper"
date: 2008-11-13
forum: Hardware
---

### Post by julienb on 2008-11-13
Hello,

I read a lot of posts here & there about the installation of Netgear WP111 usb wifi key.

But I still have a problem.

I did that:
[http://ubuntuforums.org/showthread.php?t=414023&highlight=wpn111](http://ubuntuforums.org/showthread.php?t=414023&highlight=wpn111)
but the led didn't flash anymore :-(

if I type:
```
sudo lsusb
```
I have my key listed (if I unplugged it one time, and redo the command, it isn't there anymore...)

if I type:
```
sudo ndiswrapper -l
```
I have my nice netwpn111 driver listed & my key device with the correct MAC address listed too...


I have another clue:
my usb key storage isn't detected too ...
maybe a "usb detection problem"


I'd like to know if someone could help me ?!
Should I reinstall my OS in order to reinitialize my conf ?

---

