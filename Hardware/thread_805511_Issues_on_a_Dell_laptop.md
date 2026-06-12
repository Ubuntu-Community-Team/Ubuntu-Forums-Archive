---
title: "Issues on a Dell laptop"
date: 2008-05-24
forum: Hardware
---

### Post by The Burning Fool on 2008-05-24
Okay, first things first, I am a complete newbie at this so excuse the ignorance on my part.  I had Ubuntu 7.10 installed on my previous laptop and it ran like a charm and I didn't really mess with anything.

So anyways I just got my laptop a couple weeks ago and all eager like I popped in a liveCD of Ubuntu 8.04 into the computer and booted her up.  Didn't give me any problems booting up or anything, but when I try to use my touchpad it kept right clicking whenever I dragged my finger along it and the cursor didn't respond.  "Oh well " I thought and plugged in a USB mouse.  It was detected and it worked fine.  So I go and click on the wireless icon and it doesn't give me a list of available wireless networks like it usually does on my other computer, leading me to believe that the wireless card has not been detected.

The wireless card, according to my invoice is a Dell Wireless 1395 802.11g Mini Card, and the touchpad is the generic Dell one.  Any and all help with this is most appreciated.

---

### Post by saxmaker on 2008-05-31
did you get this resolved?  I'm having the same problem with my new xps1530 dell.   no wireless unless I plug in my usb wireless and the touchpad is acting crazy!  any help would be so helpful.  I'm running a dual boot with the vista thats on it with no problems.  I don't want to use vist at all.

---

### Post by Alexis Phoenix on 2008-05-31
Hi
The wireless card is actually a broadcom card supported by the bcm43xx or b43 drivers, and you will need to install the firmware for it - hunt for "firmware" in Synaptic.

I don't know about your touchpad issue, but it is most probably a Synaptics touchpad - you should check you have the Synaptics driver for it.  In anycase, the IMPS/2 driver should work fine as a fallback - you just won't get edge scrolling etc.

HTH
Alexis Phoenix

---

### Post by ugm6hr on 2008-05-31
> **Alexis Phoenix said:**
> The wireless card is actually a broadcom card supported by the bcm43xx or b43 drivers, and you will need to install the firmware for it - hunt for "firmware" in Synaptic.


Use a cable ethernet internet connection when doing this.  It should also appear as an option in System-Administration->Hardware Drivers

---

