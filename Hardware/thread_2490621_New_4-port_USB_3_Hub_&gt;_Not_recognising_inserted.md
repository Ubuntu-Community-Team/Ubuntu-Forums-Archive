---
title: "New 4-port USB 3 Hub &gt; Not recognising inserted devices &gt;"
date: 2023-09-09
forum: Hardware
---

### Post by noobtechninja on 2023-09-09
Hi there guys.

I was hoping that you could provide some insight into a strange issue that
I've been experiencing

I've only got x2 usable USB 3 ports on the back of my PC
They get used / used up, frequently and it prevents me from using other
high speed USB 3 devices in them.

I have very recently bought a 4 port, USB hub, USB 3 speed (Type-A USB connection). To try and remedy the issue.


**Problem:**
The PC doesn't recognise devices when I put them into the new USB hub
(It's very intermittent - approx 1/8  1/10 times that a device will be recognized
and usable).


**Troubleshooting:**
1. Tried multiple different USB sticks (and powered external HDD),
in all x4 of the USB ports on the Anker hub = Same issue
(The devices do not show up on the host PC).

2. Tried both of the USB 3, ports on the PC with the Anker USB hub = Same issue

3. Tried using a USB 2 slot, the issue "appears" to go away and devices are
recognised on the Hub (I've only tried this a couple of times though).

4. Tried the Anker Hub on my Laptop (running Ubuntu 20.04 LTS) = Appears to have
worked - However, again I've only tried this twice on the Laptop.
So not an exhaustive test.


**Questions:**
1. What could be causing this behaviour ?

2. Have I bought a "lemon" ?

3. Am I missing anything (either obvious or obscure) ?


TIA for any help or advice.


**Useful details:**

USB hub:
Anker 4 port USB 3, Ultra slim version 
Model: Anker - AK-A7516012

PC details:
OS: Ubuntu 22.04 LTS
DE: KDE version 2.24.7
Kernel: 6.2.0-32-generic-(64-bit)

---

### Post by TheFu on 2023-09-09
Many devices don't work with USB hubs.  I've had problems with microphones and webcams, but sometimes with external storage devices.
You might check with Anker to see if there's a firmware update for the hub.  A 7-port USB3 hub that I had 10+ yrs ago got new firmware.  Unfortunately, the only way to update it was to using MS-Windows with a USB3 port.  I didn't have USB3 on any of my Windows computers. The vendor offered to send a replacement with the new firmware, but they wouldn't guarantee it would be mine, which was nearly new, so I declined.  Over the years, that not-so-great firmware got some drivers in Linux to make it work well-enough.

BTW, for a desktop computer, there are usually 3-5 extra USB3 headers on the motherboard which can be connected to addon ports you'd place on the front panel.  I've replaced the 3.5inch floppy slots in my motherboards with dual USB3 port adapters. These were basically passthru ports, not hubs. They run $10-$30 on Amazon.  When you look, don't go too crazy with all-in-one memory card slots and 5+ usb2 ports along with dual USB3 port setups.  These add complexity and can become devices that make booting much slower, as each USB device needs to be checked at boot for flash boot media. Say it takes 10 seconds to check each port and you have 8 of these added ports.  Having boots take 80 seconds longer isn't great.

---

