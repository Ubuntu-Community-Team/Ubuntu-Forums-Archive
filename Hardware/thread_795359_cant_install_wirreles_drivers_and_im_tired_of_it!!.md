---
title: "cant install wirreles drivers and im tired of it!!!!"
date: 2008-05-15
forum: Hardware
---

### Post by franc33s on 2008-05-15
:mad: Hi all,i have ubuntu 7.10 i even git the install cd posted to me at home i love the OS but i cant install my wirreles drivers!!!!! i mean its important for me so i can use my laptop (Acer Travelmate 2480) at hotspots. i realy cant install it! im tired of searching and searching :mad: PLEASEEEEEEE help meeeeeeeeeeeee!!!!!!!!!!!!!!!!!

---

### Post by franc33s on 2008-05-15
:(:confused:

---

### Post by prshah on 2008-05-15
> **franc33s said:**
> Hi all,i have ubuntu 7.10 
 but i cant install my wireless drivers!

Why not try my step-by-step guide (with expected outputs) ([http://ubuntuforums.org/showthread.php?t=756260](http://ubuntuforums.org/showthread.php?t=756260)) to set up your wireless network card? If you run into any problems, post back which step you are stuck at.

---

### Post by franc33s on 2008-05-15
:( i just cant understand how to do it:( i can use my wired ethernet connection at home with no problems. ndiswrapper is so confusesing me. withwindows xp or vista my wirreles works very good cant there be a easy way to make it work in ubuntu 7.10????  whats the point of having a wireles card and you cant use it?????:confused:

---

### Post by franc33s on 2008-05-15
my adapter is a AR5006EG 802.11 b/g Wireless PCI Express

---

### Post by Jordanwb on 2008-05-15
What I did (incredibly easy) is this:

1) Goto Synaptec Package Manager
2) Install ndisgtk (and required packages)
3) Insert your wifi card (Since it's a PCI-E card skip this)
4) Insert your wifi card's CDROM
5) I can't remember where it's located but it's like System->Administration->Windows Wireless Drivers

With that program your wifi card should show up and you can easily install your wifi card using Windows drivers.

Hope that helps.

BTW Why does a B/G wifi card need to be PCI-E?

---

### Post by franc33s on 2008-05-15
i think i got it working now with ndiswrapper. when i right click my network icon i see enable wirrles. i dont have a hotspot to test it now btw.:KS

---

### Post by franc33s on 2008-05-15
i have install the wirreles on my travelmate 2480 it works ok thanks for tha help :KS:)

---

### Post by Jordanwb on 2008-05-15
If my suggestion worked can you click on the Medal icon on the bottom right of my post.

You're going to have to change your signature now.

---

