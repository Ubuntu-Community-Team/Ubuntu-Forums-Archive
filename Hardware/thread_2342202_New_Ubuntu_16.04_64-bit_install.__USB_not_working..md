---
title: "New Ubuntu 16.04 64-bit install.  USB not working.  But USB 3.0 works fine."
date: 2016-11-04
forum: Hardware
---

### Post by digi84 on 2016-11-04
Hello.

I am new to Ubuntu and Linux in general.  I tried this under New Users section but might be a better fit for Hardware.

I did a fresh install of Ubuntu 16.04 64-bit.

None of my USB ports are working, except for my 2 USB 3.0.  If I plug something into the non-3.0 slots, nothing happens.  Ubuntu doesn't even recognise anything is plugged in.  They all work fine when I boot in Windows 10(I have 2 SSD hard drives.  On has Windows 10, the other Ubuntu, they do not share a SSD).

I tried buying a USB 3.0 hub -http://www.bestbuy.com/site/j5-create-7-port-usb-3-0-hub-black/4561575.p?skuId=4561575&cmp=RMX

It works.....to an extent.  I have 5 devices that connect to USB(Keyboard, Mouse, Speakers/or headphones, External HD, Wireless Internet dongle), so I think it overloads the hub, so wonky stuff happens.  Whenever the USB speakers/headphones are playing anything(MP3s, system sounds, anything) the keyboard and mouse will stop working.

Again, new to Linux so not sure what other info you might need.  I just mentioned everything I can think of.  

Any help is greatly appreciated.  Thank you!


**Update 11/6/16**

> **Temüjin said:**
> [https://ubuntuforums.org/showthread.php?t=2188370](https://ubuntuforums.org/showthread.php?t=2188370)

Thanks to everyone for the help!

---

### Post by gordintoronto on 2016-11-05
Please run this command, and paste the output into your reply: lsusb

Also, what motherboard is in this computer?

To get nicely formatted information about your computer, run these commands:
cd Desktop
sudo lshw -html >config.htm

That will place a file on your desktop, which opens in your browser. And note the upper-case "D" in Desktop.

---

### Post by digi84 on 2016-11-05
> **gordintoronto said:**
> Please run this command, and paste the output into your reply: lsusb

Also, what motherboard is in this computer?

To get nicely formatted information about your computer, run these commands:
cd Desktop
sudo lshw -html >config.htm

That will place a file on your desktop, which opens in your browser. And note the upper-case "D" in Desktop.

Thank you very much for replying! Help is greatly appreciated.  

For the lsusb this is what popped up.

```

Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 003: ID 1058:1230 Western Digital Technologies, Inc. My Book (WDBFJK0030HBK)
Bus 009 Device 004: ID 05e3:0617 Genesys Logic, Inc. 
Bus 009 Device 002: ID 05e3:0617 Genesys Logic, Inc. 
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 006: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 008 Device 005: ID 1532:0050 Razer USA, Ltd 
Bus 008 Device 004: ID 06f3:0309  
Bus 008 Device 003: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 008 Device 002: ID 2109:3431 VIA Labs, Inc. Hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

Motherboard info

```
id:[TABLE="class: node, width: 100%"]
[TR]
[TD="class: first"][/TD]
[TD="class: second"]core
[/TD]
[/TR]
          [TR]
[TD="class: first"]description: [/TD]
[TD="class: second"]Motherboard[/TD]
[/TR]
        [TR]
[TD="class: first"]product: [/TD]
[TD="class: second"]970A-UD3P[/TD]
[/TR]
        [TR]
[TD="class: first"]vendor: [/TD]
[TD="class: second"]Gigabyte Technology Co., Ltd.[/TD]
[/TR]
        [TR]
[TD="class: first"]physical id: [/TD]
[TD="class: second"]0
[/TD]
[/TR]
        [TR]
[TD="class: first"]version: [/TD]
[TD="class: second"]x.x[/TD]
[/TR]
        [TR]
[TD="class: first"]serial: [/TD]
[TD="class: second"]To be filled by O.E.M.[/TD]
[/TR]
        [TR]
[TD="class: first"]slot: [/TD]
[TD="class: second"]To be filled by O.E.M.[/TD]
[/TR]
[/TABLE]

```

Did you need anything else from that file created to Desktop or just the mobo info?

---

### Post by gordintoronto on 2016-11-05
That's puzzling! Ubuntu sees numerous USB 1.1 and 2.0 ports, but you say they don't work? So, for example, if you plug a mouse into one of those ports, it doesn't move the cursor?

I'm baffled.

---

### Post by Bucky Ball on 2016-11-05
Get rid of the hub!

Pull that hub out, hide it somewhere and do not use it for these tests. Any commands you are asked to run, do not do so with the hub plugged in. Thanks. ;)

Trying to get appropriate information when running commands or trying to fix with that hub plugged in just confuses the issue. You don't need it, you don't need a workaround, you need to find a fix for your existing problem, which is an odd one but no doubt you'll get there. :)

---

### Post by Yellow Pasque on 2016-11-06
[https://ubuntuforums.org/showthread.php?t=2188370](https://ubuntuforums.org/showthread.php?t=2188370)

---

### Post by Bucky Ball on 2016-11-06
> **Temüjin said:**
> [https://ubuntuforums.org/showthread.php?t=2188370](https://ubuntuforums.org/showthread.php?t=2188370)

Great find. Let's hope that solves it. :)

---

### Post by digi84 on 2016-11-06
> **Temüjin said:**
> [https://ubuntuforums.org/showthread.php?t=2188370](https://ubuntuforums.org/showthread.php?t=2188370)


Worked perfectly!  Thank you so much!

---

