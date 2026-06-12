---
title: "Logitech Revolution Laggyness"
date: 2006-12-01
forum: Hardware &amp; Laptops
---

### Post by NitrousUK on 2006-12-01
Has anyone else had problems with the Logitech Revolution MX in that it randomly freezes now and then, sometimes for a split second sometimes for a couple. It seems intermittant and random and fairly frequent, perhaps a few times every minute. I havent been able to search for anyone else having this problem. I've tried dif USB ports and it works fine on my laptop. Any help/info greatly appreciated, thanks.
My specs are:

Core2Duo E6600@2.66ghz
2GB Corsair Dominator 8500@1ghz
Asus P5W DH Deluxe mobo
Gigabyte 7600GT
Western Digital 320gb SATA RE
Hiper 580W PSU

---

### Post by futz on 2006-12-01
> **NitrousUK said:**
> Has anyone else had problems with the Logitech Revolution MX in that it randomly freezes now and then, sometimes for a split second sometimes for a couple. It seems intermittant and random and fairly frequent, perhaps a few times every minute. I havent been able to search for anyone else having this problem. I've tried dif USB ports and it works fine on my laptop. Any help/info greatly appreciated, thanks.
Mine does that too. Mildly annoying. I assume it's the mouse power-saving feature kicking in, but I'm not sure. I should move it to a windows box for a day and see if it does it there too. Will let ya know if and when I do that.

Even with that little annoyance I still love this mouse a lot. Old style scroll wheels seem so... krungy now. :mrgreen:

EDIT: > I assume it's the mouse power-saving feature kicking in, but I'm not sure.
Nope. That's not it. It happens in mid-freewheel-scroll often.

---

### Post by NitrousUK on 2006-12-02
Does it in Kubuntu too and both of them fresh installs. I find it hard to believe others arent having the same probs as the revolution should be fairly popular, what motherboard do you have futz?

---

### Post by futz on 2006-12-02
> **NitrousUK said:**
> Does it in Kubuntu too and both of them fresh installs. I find it hard to believe others arent having the same probs as the revolution should be fairly popular, what motherboard do you have futz?
Only the best for me! :mrgreen: This box runs a DFI LANPARTY UT nF4 Ultra-D
[http://us.dfi.com.tw/Product/xx_product_spec_details_r_us.jsp?PRODUCT_ID=3471&CATEGORY_TYPE=LP&SITE=NA](http://us.dfi.com.tw/Product/xx_product_spec_details_r_us.jsp?PRODUCT_ID=3471&CATEGORY_TYPE=LP&SITE=NA)

---

### Post by NitrousUK on 2006-12-03
You've got an nforce4, ive got an intel 975 chipset, seems like its not a chipset issue, what else could be causing it!? :s maybe its the usb controller chipset. Out of curiousity, are you running the AMD64 version of kubuntu/ubuntu?

---

### Post by futz on 2006-12-03
> **NitrousUK said:**
> are you running the AMD64 version of kubuntu/ubuntu?
Nope. i386.

I tried the 64 bit a while back. Stuck with it for 3 or 4 days, then wiped the drive and reinstalled with the 32 bit version. Too many little problems with 64.

---

### Post by futz on 2006-12-29
> **NitrousUK said:**
> the Logitech Revolution MX in that it randomly freezes now and then, sometimes for a split second sometimes for a couple.
I just happened to rebuild a crappy lightweight windows box that's on the same KVM as my Ubuntu box with the MX Revolution. The machine is a P4 1.7 Celeron midget box (865 chipset) that I found in a dumpster (the general contractor on the job saw it get chucked and, knowing I'm a computer geeky type guy :mrgreen:,  pointed it out to me). It just needed a new mainboard and some TLC. It was buried under about three feet of landscape waste, mud and sticks. Got a legit xp home license out of it though (they left the decal on the box), which was definitely worth the dig. But I digress...

I notice the exact same little blips on the windoze box as in Ubuntu. Seems it must be something to do with the mouse itself, not the OS.

---

### Post by drdrewusaf on 2006-12-30
Mine, also, has the same "problem" in both winxp and ubuntu.  Probably a mouse hard/firmware issue then?


Drew

---

### Post by futz on 2006-12-30
> **drdrewusaf said:**
> Mine, also, has the same "problem" in both winxp and ubuntu.  Probably a mouse hard/firmware issue then?
Most likely some little glitch in how they transmit packets over the wireless connect. This thing is RF, not infrared like most wireless mice.

---

### Post by po0f on 2006-12-30
futz,

Do you have anything that creates a lot of noise?  I don't know how RF works; all I know is that my MX Revolution is working perfectly, no lag, no skipping.

---

### Post by futz on 2006-12-31
> **po0f said:**
> futz,

Do you have anything that creates a lot of noise?  I don't know how RF works; all I know is that my MX Revolution is working perfectly, no lag, no skipping.
Nothing very obvious. There is a compact fluorescent desk lamp between the tranceiver dongle and the mouse. I'll experiment with an incandescent bulb for a while and report back...

RF == Radio Frequency. It's probably pretty similar to bluetooth. Just a simple low power radio link between mouse and dongle.

---

### Post by po0f on 2006-12-31
futz,

I know what RF is, just not how it works.

Doesn't the MX Revolution operate at 2.4GHz?  And don't most wireless cards operate at the same frequency?  Maybe this is part of your problem.

[EDIT]

I don't own a wireless card so maybe that's why I'm not experiencing any problems.

---

### Post by futz on 2006-12-31
> Doesn't the MX Revolution operate at 2.4GHz? And don't most wireless cards operate at the same frequency? Maybe this is part of your problem.
LOL! :mrgreen: Hope that's not the problem. I've got 3 wireless cards as well as 3 wireless routers in this room.

Right now it looks like it might have been that compact fluorescent sitting about 16" from both the dongle and the mouse. It'll take longer term testing to be sure, but I haven't noticed any blips since I changed bulbs.

---

### Post by drdrewusaf on 2007-01-02
Actually, if they are both on 2.4Ghz, that could be the problem.  RF signals that are on the same freq or on a sideband of that freq can really cause some bad interference.  Thats the reason a lot of RC cars come with either a channel/freq switch or a warning about using two of the cars in close proximity...

I only use my wireless network for my laptop, but my MX is on my desktop.  I've never noticed if, when the laptop was using the network, the mouse had more or less lagginess/pauses.

Of course, when I built the desktop I was reeeeeeeeaaaaaaaalllllllllyyyy into air cooling...too cheap for water cooling.  So I have somewhere around 900 (9 in reality) fans.  Electric motors cause RF interference, not in the 2.4Ghz rang though....




Drew

---

### Post by Pondlife on 2007-02-07
[FONT="Verdana"]I've been using my MX Revolution for several weeks with no problems, but recently activated my WLAN for someone and the mouse now skips and stutters randomly.  Can sometimes go for a few minutes without a stutter, but then may hang for 5 seconds before returning to life.

Have found that both my router and the mouse operate within the 2.4GHz frequency range, and plan to try altering the frequency slightly of the router (between 2.41-2.49GHz) to see if it helps.  Haven't yet determined the exact frequency of the mouse though?

If this doesn't help I've narrowed the options down to:

1) Turn off the WLAN
2) Replace WLAN router
3) Line the room with tin-foil to reduce the WLAN signal :) 
4) Purchase a USB hub and place closer to the mouse, hoping signal improves
5) Replace with wired mouse[/FONT]

---

### Post by chunger on 2007-02-09
> **NitrousUK said:**
> Has anyone else had problems with the Logitech Revolution MX in that it randomly freezes now and then, sometimes for a split second sometimes for a couple. It seems intermittant and random and fairly frequent, perhaps a few times every minute. I havent been able to search for anyone else having this problem. I've tried dif USB ports and it works fine on my laptop. Any help/info greatly appreciated, thanks.


I have sort of the same problem, the mouse just seems to quit suddenly, and intermittently (happens in XP too).  Since practically all my neighbors are running 2.4ghz wireless routers (myself included) I suspect that this might be the cause (not to mention the cordless phones) since the mouse also operates on the same frequency... although not sure on what channel.  
Pain in the butt as it is, I found that pulling the USB receiver out and plugging it back in seems to gets the mouse going smoothly again... till the next time it happens that is.

---

### Post by wonko on 2007-05-11
I also have this problem. Living in a block apartment, I don't know wether my neighbours use wlan, but changing channel on my own router, or turning the wireless-option off, didn't make any noticeable difference. I think maybe re-plugging the dongle helped a little though...

---

### Post by coredix on 2007-05-21
Hi, i had this problem under windows in any available usb-port.
No wireless lan or bluetooth devices installed.

While installing feisty on the same machine it turned out, that a faulty usb-hub was the source of all troubles - even if the receiverstick was connected directly to the mainboard ports.
The hub causes usb bus scans every now and then, because the connected devices randomly got no /  or lost their IDs.
After disconnecting the hub everything was fine.
Maybe a better usb-cable could do the trick either, there are many bad shielded cheap AWG28x1p / AWG28x2c in the shops.

If you are lucky a better shielded extension cable, with AWG28x1p/AWG24x2c plugged directly to the mainboard port and receiverstick placed near your Revo could help against any RF interferences.

coredix

---

