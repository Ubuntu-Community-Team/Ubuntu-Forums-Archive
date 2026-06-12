---
title: "HP G60 213EM laptop compatibility?"
date: 2009-04-24
forum: Hardware
---

### Post by ajgreeny on 2009-04-24
I am looking at an HP G60 213EM laptop [http://h10010.www1.hp.com/wwpc/uk/en/ho/WF02a/321957-321957-3329743.html](http://h10010.www1.hp.com/wwpc/uk/en/ho/WF02a/321957-321957-3329743.html) and wonder if anyone has used ubuntu on this model. and if so how it worked.  The one thing I can't find info about on HP's website is the wireless chipset, so can't help there, but it has an intel graphics card which I think should be good, and possibly an intel wireless card, but that is to be confirmed, I hope, by HP, whom I have emailed.  Here's hoping!

---

### Post by luig1 on 2009-04-24
I have used ubuntu 8.04 on a HP g60 laptop before but it isnt compatibles straight out of the install. For example after you install ubuntu you will need to configure the wifi drivers and the video drivers. Everything else pretty much works.

---

### Post by ajgreeny on 2009-04-25
Thanks for that, Luig1.
When you say "configure drivers" I presume you mean in the *System > Administration > Hardware Drivers* from the menus.  If that is correct, it is what I expected to be needed, but I just wanted to make sure as far as possible that there was no need for compiling of wireless drivers, in particular, as I might find that a bit of a chore.
What wireless chipset did your machine have?

---

### Post by luig1 on 2009-04-25
You have to compile cutom drivers don't worry it takes less than a minute. the instructions are right [here]("http://blog.hyperandy.com/2008/11/01/atheros-ar242x-ubuntu-810-ibex/"). Btw it took me 3 hours to search for these instructions. As for the intructions for the video driver configuration I look them up later for you. I am installing Ubuntu 9.04 on my G60 laptop. I'll have the results for you in a few hours. Oh and the chipset is an Atheros.

---

### Post by ajgreeny on 2009-04-25
Great!  Thanks for the quick response.  I will now wait and see if the chipsets are as you say, or if, as often happens, they have now changed them to something more linux friendly.  I will also be very interested to hear how you get on with 9.04 on the laptop before I go ahead and purchase one.

Thanks again.

EDIT:   Looking at the driver downloads page of HP it seems the wireless drivers are either Intel or Broadcom, but whether this means that they are not Atheros chips, I really don't know.  I just find it very annoying that it is so difficult to find such details on the computer manufacturer's page, but I suppose most people never need to know, do they?

Intel PRO/Wireless Drivers for Microsoft Windows Vista
    Date 02-2009     Version 8.20          5.58M
Broadcom Wireless LAN Driver for Microsoft Windows Vista
    Date 02-2009     Version 7.20          18.74M

---

### Post by luig1 on 2009-04-25
Ok I just finished installing Ubuntu and configuring everything. I am now typing this on my HP G60 laptop and to my suprise Ubuntu 9.04 did not have any problem with wifi. I only had to install the latest NVIDIA drivers which was a piece of cake. Also what I liked about 9.04 is that it not only gave me working wifi drivers it also gave me the option to switch madwifi driver which support monitor mode(Monitor mode is used for capturing packets to crack wep keys and to inject packets).

---

### Post by ajgreeny on 2009-04-27
That's great, though it looks as if your machine has different graphics and wireless adapter to the one I've found.  Good to hear that it works for you though, and If I get one, I'll be sure to let you know how things went.

---

