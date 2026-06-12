---
title: "ipw2200: Radio Frequency Kill Switch is On - how do i turn it on in edgy?"
date: 2006-11-19
forum: Hardware &amp; Laptops
---

### Post by yeehawjared on 2006-11-19
Dapper worked great with my intel pro wireless IPW2200.  I just did a clean install of edgy and my iwp2200 is detected, but doesn't enable.

here's my dmesg | grep ipw2200 output:

```
root@jaredtop:~# dmesg | grep 2200
[17179573.220000] usbcore: registered new driver usbfs
[17179573.220000] usbcore: registered new driver hub
[17179582.516000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.2kmprq
[17179582.516000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[17179582.516000] Driver 'ipw2200' needs updating - please use bus_type methods
[17179582.516000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection[B][COLOR="Red"]
[17179583.248000] ipw2200: Radio Frequency Kill Switch is On:[/COLOR][/B]
[17179583.248000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)

```

Funciton + F2 does not turn it on... When I boot into XP my ipw2200 works great.  How can I enable this?

I have a dell inspiron 9300 and have talked to other users with the same problem... any solutions would be greatly appreciated.  :)




[COLOR="Red"]EDIT: I GOT MY CARD WORKING!
Here's how i did it:

[http://www.ubuntuforums.org/showthread.php?t=26623&highlight=ipw2200](http://www.ubuntuforums.org/showthread.php?t=26623&highlight=ipw2200)

download the ieee and ipw2200 tar's

follow the directions - remove the old drivers, make the new ones

reboot and you're good to go.  money[/COLOR].

---

### Post by yeehawjared on 2006-11-19
I guess I really mean how do I turn OFF the kill switch.  Sorry about that confusion.

---

### Post by yeehawjared on 2006-11-22
bump 8)

---

### Post by Buffalo Soldier on 2006-11-22
Have you tried checking the options in BIOS for your Wifi card? For my laptop (DELL Inspiron 510m) these are the options:[list]
[*] Off
[*] Controlled by OS
[*] Controlled by OS **or **FN Key  <<-- I choose this
[/list]

---

### Post by yeehawjared on 2006-11-22
hooray!  i got my wireless working.  Here's how i did it:

[http://www.ubuntuforums.org/showthread.php?t=26623&highlight=ipw2200](http://www.ubuntuforums.org/showthread.php?t=26623&highlight=ipw2200)

download the ieee and ipw2200 tar's

follow the directions - remove the old drivers, make the new ones

reboot and you're good to go.  money.

---

### Post by nereocystis on 2007-11-06
I have a Dell 1420N.

the radio frequency kill switch is a switch on the front of the laptop, underneath the status lights.  I accidentally switched it to the left, which cut off my wireless.  Eventually, I switched it to the right, which enabled the wireless.  The wireless status light did turn on and off, but I didn't notice.

---

