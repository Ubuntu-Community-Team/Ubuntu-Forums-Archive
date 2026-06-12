---
title: "Maverick - Bluetooth DiNovo Edge won't work"
date: 2011-01-17
forum: Hardware
---

### Post by Random21 on 2011-01-17
Short of it:  

I cannot get my dinovo edge to connect.  I can connect it to my pc at work, but the OS has to do the search to find it, the keyboard does not have the "connect" button.

Story:

I bought this on eBay.  Turns out it is both grey-market and is the "Mac edition" with some generic bluetooth dongle thrown in.


What I've tried:

I did some searching and did the edit of /lib/udev/rules.d/70-hid2hci.rules (changing hiddev to hidraw or vice versa).  This did not help.

Unplugged and plugged the dongle back in, rebooted, repeated, etc.

Tried to use the bluetooth applet, but whenever I click "turn bluetooth on" it just seems to hang.

Killed bluetooth applet, restarted, and tried all that jazz again.

Information I know:

I have a bluetooth address on the back of the keyboard.
lsusb lists the dongle as:
Bus 005 Device 006: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode).


Can anyone provide any help or any information that might be useful please?

Thanks.

---

### Post by Random21 on 2011-01-18
Update:

hcitool dev would not detect the dongle. I eventually got it to work by changing the BIOS setting to "Plug and Play OS."  Now hcitool dev detects the dongle but hcitool scan won't pick up the keyboard.

My phone can pick up the keyboard.  When I have both my phone and hcitool scanning neither will detect the other.  I don't understand bluetooth well enough to know if that's important.

---

### Post by Random21 on 2011-01-20
I now have it working.  I will occasionally have to unplug and re-plug the dongle on boot to get it to work.  I don't know exactly what I did.

I downloaded bluez and now I have both the bluetooth applet running and bluemon running.  Weirdest thing is that it would pick up my keyboard occasionally.  Then not at all, then it started connecting.  It gave me a pin to type in on my keyboard to connect it and it would not connect if I hesitated at all (we're talking like less than 10 seconds).

I don't know how exactly I fixed it but if anyone else has this problem feel free to post here and I will stay subscribed and try to help.  I don't know much though.

---

### Post by splash_ on 2011-01-31
Hey man.

This issue was solved here: [http://ubuntuforums.org/showthread.p...uetooth&page=1](http://ubuntuforums.org/showthread.p...uetooth&page=1)

In a nutshell: you need to upgrade your bluez package. 

I wrote about it here: [http://mylabsk.blogspot.com/2011/01/...code-with.html](http://mylabsk.blogspot.com/2011/01/...code-with.html)

Good luck!

---

