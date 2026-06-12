---
title: "Replacing monitor - how?"
date: 2007-01-13
forum: Hardware &amp; Laptops
---

### Post by johann_p on 2007-01-13
I am going to replace my old CRT Nokia with an EIZO [FONT=Arial, Verdana, Helvetica, sans-serif][SIZE=3]FlexScan S2110W-BK.

How should this be done? Will Ubuntu automatically detect and set up the monitor correctly when I boot? This will have a different resolution and different aspect ratio, so is there anything to be done except replacing the hardware?

Last time when I replaced the mouse, I had problems because Ubuntu did not detect the different resolution (and has still problems on the login screen), so I would like to avoid unpleasant surprises.
[/SIZE][/FONT]

---

### Post by bigken on 2007-01-13
in a terminal you run dpkg-reconfigure xserver-xorg if its not auto detected ;)

---

### Post by johann_p on 2007-01-18
Thanks for that info. I just wonder how one is supposed to know that? I mean, people say about Ubuntu that it is so user friendly, but how is a simple user supposed to find this out without the help of the friendly people here?

I installed the screen and after reboot, the same information was in the xorg.conf file, the monitor name was still the same etc. so Ubuntu did not detect the change or do anything about it.

I then used the reconfigure command and the result was disappointing: the combination of that screen resolution (1680x1050) looked extremely fuzzy and crappy on my high-end EIZO monitor.

It turned out that Ubuntu installs a very old version of the NVidia driver ... going to this repository [http://www.albertomilone.com/drivers](http://www.albertomilone.com/drivers) and downloading the latest driver (I need the latest legacy driver) made all the difference. But again, something that I could only figure out with the help of people here -- Ubuntu did nothing to make this easy for me :(

(just for comparison: there is a yum repository for OpenSuse directly on the NVidia server)

I do not know whether developers are aware about these things, but after using Ubuntu for quite some time, my impression is that especially when it comes to changing things there is a lot that is missing to make Ubuntu really "easy" -- not only when compared to Windows, but also when compared to other distros.

---

