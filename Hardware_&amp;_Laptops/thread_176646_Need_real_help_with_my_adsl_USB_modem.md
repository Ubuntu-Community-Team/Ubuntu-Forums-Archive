---
title: "Need real help with my adsl USB modem"
date: 2006-05-15
forum: Hardware &amp; Laptops
---

### Post by Bulltitan on 2006-05-15
Well i have ubuntu installed in a second partition and seems to be that the
only two problems i have so far are,... the usb modem not recognized at all (huauei MT810) and my ati 9600 se card,... but first things first. I really need the internet connection to work, i'm new to ubuntu, not linux really cos i've been around Xandros 3 and mandrake 9 but i still have a lot to learn about this kind of os and please be gentle  with me, i used to be a windows xp child :p .

---

### Post by mips on 2006-05-15
[http://www.ubuntuforums.org/showthread.php?t=43377&highlight=MT810](http://www.ubuntuforums.org/showthread.php?t=43377&highlight=MT810)
[http://forum.eagle-usb.org/viewtopic.php?t=4010](http://forum.eagle-usb.org/viewtopic.php?t=4010)
[http://atm.eagle-usb.org/wakka.php?wiki=UeagleAtmDoc](http://atm.eagle-usb.org/wakka.php?wiki=UeagleAtmDoc)
[http://faq.eagle-usb.org/wakka.php?wiki=InfoCMVEn](http://faq.eagle-usb.org/wakka.php?wiki=InfoCMVEn)
[http://packages.debian.org/unstable/net/eagle-usb-utils](http://packages.debian.org/unstable/net/eagle-usb-utils)
[http://dev.eagle-usb.org/wakka.php?wiki=EagleUsb230](http://dev.eagle-usb.org/wakka.php?wiki=EagleUsb230)

---

### Post by Bulltitan on 2006-05-16
Thanks for the links but after that i'm still getting the:
error :Unknown error 512
failed to send options to device /proc/bus/usb/002/005
after "$ sudo eaglectrl -w", i don't know what's going on with this. ](*,)

---

### Post by Bulltitan on 2006-05-24
Ok the modem is working fine i've done this by installing the eagle-usb-2.3.2 driver and also rp-pppoe in the latest version you can get, 
but after all the compiling, and installing thing theres yet another issue. Whenever i reboot or shutdown the system and while ubuntu is booting i see the link light flashing but seems that it can't get syncro, so what i do is "eaglectrl -d" then "eaglectrl -w" sometimes 
i get the syncro right there but if not i have to unplug the modem and plug it back in and even if i get syncro there i can't connect to the
internet rp-pppoe gui gives me "connection timed out". I have check all the settings inside "eagle-usb.conf" "eagle-usb.conf.template" also "resolv.conf" and "pppoe.conf" and everything it's ok.
I know that this is not the right way to get the modem syncronized and ready
to be opeartional but i can't find any other way to doit, any ideas? ](*,)

---

