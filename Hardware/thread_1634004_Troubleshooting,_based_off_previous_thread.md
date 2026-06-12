---
title: "Troubleshooting, based off previous thread"
date: 2010-11-29
forum: Hardware
---

### Post by ghost25 on 2010-11-29
Hey guys, I'm back.

I ended up not bothering with testing some of the suggested ideas for the Acer Aspire 5570z, due to insufficient time and energy. However, I did buy a Compaq Presario CQ62, running (of course...) Win7. Celeron processor, 2GB RAM, the usual.

I just swapped hard drives, removing the known good drive running Windows 7 and putting that in the Acer, with no results; apparently I did indeed either fry, crack, or otherwise break something inside on the motherboard. Whatever... it's too time-consuming at the moment to figure out, considering the Acer, regardless of drive when I power it on, won't reach POST or any other diagnostic screen, merely sits there like a lump on a log after the processor LED stops. That's neither here nor there.

My question ATM is, putting in the Ubuntu drive from the wrecked Acer into the new Compaq, it powers up after a short time, and lets me use the touchpad to select the user, but I can only click using the little click-bar. I cannot, however, use either onboard or external USB keyboard to type, at all. No NumLock key illumination, no caps lock, nothing. No response when I type.

Sticking with the Compaq here...

I currently have the Compaq running off a Knoppix LiveCD, and no problems with the mouse moving but cannot click on anything. Using the Ctrl+Alt+F1 I am able to get to CLI and navigate just fine, however the mouse does not transmit clicks. 

As I type commands in CLI however, I find that I must type each key twice. Eg, if I want to view contents of the directory I am in, I must type "llss" instead of "ls" as it does not register the first keystroke.

I am assuming something got seriously borked here, either on the hard drive itself or something just broke in the actual kernel from the unexpected damage, however at this point I'm going off nothing more than an educated guess.

I am unable to restart without a hard reset, even allowing for the "knoppix wheelmouse us" commands to allow for said wheelmouse. Upon reset, I am faced with "/init: exec: line 589: /sbin/init: Input/output error".

Any ideas? Am I going to have to re-install Ubuntu? Or does the community at large have any ideas I could try?

EDIT: I figured out why I got the "input/output error" code from earlier, my disk is scratched so that, too, is hit-and-miss. So ignore that. Thanks.

---

