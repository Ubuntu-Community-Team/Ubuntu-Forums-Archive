---
title: "A Compatible Printer"
date: 2022-02-05
forum: Hardware
---

### Post by agemini68 on 2022-02-05
I just bought an HP laser jet pro MFP M29w. It's a monochrome printer that uses toner instead of ink. Worked out of the box plugged in with USB. Scanner picked it up, but when it gives you the list, you need to pick the right one and it scans nicely. For some reason Document Scanner gave me 3 different versions of my All In One and if you don't pick the right one, it can't connect. I included a screen shot with the one I had to pick for the scanner. 

I can't speak for the wireless connection due to my provider, which is T-Mobile. Their routers don't have WPS and HP didn't include a lan connection on the printer so I can't even set it up. I'm sure it would work fine if you have a router with WPS.

---

### Post by brian_p on 2022-02-05
A very informative post, agemini68. To help you and other users understand what is going on, it would very useful to have the outputs of ```
scanimage -L
``` ```
airscan-discover
``` Your Ubuntu version is also needed.

---

### Post by agemini68 on 2022-02-06
Using Ubuntu 21:10 but I'm sure you won't have a problem with others.

---

### Post by agemini68 on 2022-02-06
I'm not sure how that output from the terminal helps you, but I'm not quite as tech savvy as some of you on here, I'm the one usually requesting help.:lolflag:

---

### Post by brian_p on 2022-02-07
> **agemini68 said:**
> Using n but I'm sure you won't have a problem with others.

What you experienced works courtesy of **ipp-usb** and **sane-airscan**. Both packages are on Ubuntu 21:10 by default and auto-setup a modern USB scanner such as the HP Laser Jet Pro MFP M29w. A user has nothing to do. 

The packages  are not shipped with Ubuntu 20.04.

---

### Post by brian_p on 2022-02-07
> **agemini68 said:**
> I'm not sure how that output from the terminal helps you, but I'm not quite as tech savvy as some of you on here, I'm the one usually requesting help.:lolflag:

Having the info would allow the HP Laser Jet Pro MFP M29w to be added to the list of working devices at [https://github.com/alexpevzner/sane-airscan](https://github.com/alexpevzner/sane-airscan). This would help other users.

You could add it yourself by raising an issue, of course :).

---

