---
title: "Ubuntu 10.10 and Intel 2200bg Mini-PCI"
date: 2011-01-15
forum: Hardware
---

### Post by BenSeager on 2011-01-15
I'm an experienced Windows user but a complete newbie when it comes to Linux.  I've got an old laptop and thought I'd try it out.  I chose Ubunutu because it seems to be the one which will work out of the box most of the time - allowing me to learn how to use LInux relatively easily.

The good news - almost everything works!

The bad news - the only thing that doesn't is the wireless connection.

The laptop has an Intel 2200bg Mini-PCI WLAN card.

Using the default network applet in Ubuntu and WICD network manager I can see available networks but when I try to connect to mine it either will not connect because it fails security authentication (WPA2-PSK) because of a bad password (yes I've checked that I've typed it correctly!) or because it cannot obtain an IP address (it only does this if I disable security to test the connection).

Any help greatly appreciated!

---

### Post by middle_road on 2011-01-15
me too! me too!

I yanked out a broadcom card and installed a 2200bg thinking (assuming) it would get picked up as easy as my other laptop,
but it didn't - yet.

still searching - there's alot of chaff out there...:p

_mr

### Success! ###
I think that posting on the forum here did it... :)

I went back after posting and checked the logs - the driver was being initialized properly.
So then I just powered the wireless ON/OFF (<FN><F2> on dells) several times and after the
third cycle my access points showed up. good to go.

---

