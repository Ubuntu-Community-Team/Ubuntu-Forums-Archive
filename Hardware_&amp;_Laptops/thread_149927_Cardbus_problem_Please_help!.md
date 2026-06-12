---
title: "Cardbus problem Please help?!"
date: 2006-03-24
forum: Hardware &amp; Laptops
---

### Post by Henry Rayker on 2006-03-24
Ok, so I spent much time trying to get my PCMCIA wireless card to install, but nothing I did could get the dang card recognized by the system. I know the card's not to fault, because it works in Windows XP, on the same computer...so all hardware is functional.

Here's a problem, though, I think my cardbus is just inactive in Ubuntu. I've tried another cardbus card and it too was not seen as being plugged in. This is incredibly frustrating.

The laptop, I bought from UnitedMicro.com. I don't know a whole lot about it, but I can provide relevant printouts, if needed. I think the cardbus slots are made by 02 Inc., if that helps at all...

please help a newbie get his poor Ubuntu install wireless. My girlfriend is sick and tired of my stringing an ethernet cable around the apartment.:rolleyes:

---

### Post by IYY on 2006-03-25
You need to tell us exactly which card it is. Many wireless cards can't work in Linux without the ndiswrapper.

---

### Post by Henry Rayker on 2006-03-25
It's not the card, though, that's the point.

ANY card I've put into the slot will not show up to the system.

Just about EVERY tutorial on installing a driver for the card involves an lspci to get the chipset of the card. When I do an lspci, I don't get an output corresponding to my card, so I can't even start from there.

However, if it really matters, it is an Airlink 101 MIMO card...rt61 chipset. I've had the driver installed, though, but the hardware is undetected. I forget the command, but I think it's an ndiswrapper -_  where _ corresponds to a letter (I'm sorry, I'm on my XP install at the moment) but, it is to confirm that both the hardware and the software arepresent...my output just says driver present (no mention of hardware).

I hope I've made sense. Hopefully someone can help me out.

Thanks for your reply, though.

---

### Post by Henry Rayker on 2006-03-25
I've searched and can't find anything on this problem. Am I the only one with this problem?

---

### Post by philipreggie on 2006-03-26
I am having the same probme with Airlink card..i tried the ndswrapper to get the windows driver to work..it did download the driver but still willnot  recognize the card.
Anybody with any sugesstions.pls

---

### Post by Henry Rayker on 2006-03-27
have you been able to get to any other PCMCIA cards to check if it's the cardbus or just the card?

I mean, the 2 cards I borrowed (one was a modem, the other was a USB, I believe) COULD have been broken, but I just don't know...

---

### Post by Henry Rayker on 2006-03-30
still no one knows?  D:

---

