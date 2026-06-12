---
title: "wireless listed in lsusb, but not lspci (NOT WORKING)"
date: 2009-06-12
forum: Hardware
---

### Post by qhimq on 2009-06-12
ubuntu 9.04, hp tx1000, i remember it was working on a broadcom43x driver.


no network controller is listed in lspci, but 

Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]

shows up in lsusb. It disappears if I slide the wireless switch, reappears if I slide the switch again.  So I figure the card is connected correctly, and its a driver problem.

I've tried installing ndiswrapper and using bcmwl5, but the gui said no hardware detected (Admin->Windows Wireless Drivers).

This problem may have been caused by me installing vmware server 2, however the problem is inconsistent because some boots -actually work out and I connect to wireless networks consistently-.  I was also uninstalling and reinstalling virtualbox a million times.  Sometimes I would remove things manually since the apt-get remove doesnt get everything.

EDIT: I just looked at my bios to see if the network card was enabled, and it wasn't! So I enabled it, booted, and nothing different.  I also put it in a earlier boot order than the usb devices and...nothing.

anyone come across this issue?

---

### Post by qhimq on 2009-06-14
So my tx1000 has heating issues too.  I had it running around 85C for a maybe a few hours for each day for three days.  The fourth day I realized I did not have wireless.  I was using a wired connection all those days.

Think it got too hot?  Or some surge got to it which was caused by the heat? (i am guessing no)


I tried out the following today:
[http://forum.tabletpcreview.com/showthread.php?t=8875](http://forum.tabletpcreview.com/showthread.php?t=8875)

While taking off the wireless card, i noticed the card was firmly connected and no wiring problems with it that I could see.  there is little chance of it being a wire problem because I didn't see any pinched or burned wiring.

I didnt take off the factory thermal gease and replace it because I didnt have any on hand.  However I found a huge dust bunny, and I took off the black paint on the fins.  

Results:
Before- Idle Performance(2.2Ghz): 65C
After - Idle Performance(2.2Ghz): 73C

Now the heat up / cool down just pikes, when before it took a few seconds. 
The cool down is super good.  It goes from 73C to 51C immediately when switching from performance to power saver(800Mhz).  The heat up is just as extreme.

So I figure I must have either screwed up one of the seats for a unit that needs thermal gease.  Do you all think the application of thermal gease would make that much of a difference?

---

### Post by qhimq on 2009-06-23
so my wireless is consistently not showing up in lspci but is found in lsusb.  Why is it recognizing it as a usb device?

---

### Post by Favux on 2009-06-24
Hi qhimq,

Sorry, don't know the answer.  I'll keep an eye open.

I know this is off topic, but we've tried to follow your HOW TO to get evtouch working in Jaunty and are stuck.  Could you bail us out?:  [http://ubuntuforums.org/showthread.php?t=1040872&page=2](http://ubuntuforums.org/showthread.php?t=1040872&page=2)

---

### Post by qhimq on 2009-06-26
hi, favux.

Yeah I don't think I'll keep this post going.  I think its a hardware issue.  I have no clue where it is though.  If its the card...or the connectors... or the wiring.  I assume its not the motherboard because the wireless card goes into this huge wiring collection with other devices then connects to the motherboard, and of course those other devices work.

---

### Post by Favux on 2009-06-27
Hi qhimq,

A blown capacitor?  That should be easy to identify on the card.  You did say you had a heat problem right?  That tends to age capacitors in a hurry.

---

