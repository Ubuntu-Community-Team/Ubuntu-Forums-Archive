---
title: "WG511 v1 Adapter Install Issues in Xubuntu"
date: 2007-03-09
forum: Hardware &amp; Laptops
---

### Post by Leon2ky on 2007-03-09
I've currently got Xubuntu 6.10 installed on a Pentium III 1Ghz Toshiba laptop.  I'm currently using a Wireless adapter by the name Netgear WG511 and I have followed the instructions in the following 2 threads:

[http://ubuntuforums.org/showthread.php?t=226652](http://ubuntuforums.org/showthread.php?t=226652)
&
[http://www.ubuntuforums.org/showthread.php?t=156228](http://www.ubuntuforums.org/showthread.php?t=156228)

Now everytime I do the command:
```
sudo ndiswrapper -i netwg511.inf
```
It gives me the following message:
```
netwg511 is already installed. Use -e to remove it
```

But if I do the command to remove it it out puts this:
```
Driver netwg511.inf is not installed. Use -l to list installed drivers
```
So when I do that it out puts this:
```
Installed Drivers:
netwg511 invalid driver!
```

Right now my laptop is on a wired connection bot 75% of the time it's on wireless so I really need to get this up and running.  This particular Wireless Adapter was made in China.

---

### Post by Leon2ky on 2007-03-09
Okay I managed to get the device properly installed (I had to uninstall ndiswrapper and reinstall it) and it sees my card correctly but now I can't get it to connect to any network, and the lights on it don't even blink.

---

### Post by Leon2ky on 2007-03-09
Okay I checked dmesg and it's reporting:

```
prism54: Your card/socket may be faulty, or IRQ line too busy :(
```

I was running this PC with Windows XP before without any problems, why would I be having problems now?

---

