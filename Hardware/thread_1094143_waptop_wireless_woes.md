---
title: "waptop wireless woes"
date: 2009-03-12
forum: Hardware
---

### Post by iwizard on 2009-03-12
I upgraded my mother's laptop to ubuntu 8.10 from Windows XP.  Everything works brilliantly and she loves it ( she's only slightly computer literate - she knows how to turn it on ) save the wireless card.  It uses a Broadcom based card and I've googled countless "assistance" guides.

Nothing works, so far.  The first attempt was the quickie Activate New Hardware.  The broadcom is correctly identified but the computer locks up when I click the activate button.

Any other ideas and a little luck would be appreciated.

Thanks in advance,

Ketchup

---

### Post by bailbath on 2009-03-12
Here are a couple of links for you hope it helps you.
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom)

[http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)
Ian

---

### Post by Simian Man on 2009-03-12
Elmer, can you tell us which card you have exactly?  Post the output of
```

lspci | grep roadcom

```

---

### Post by iwizard on 2009-03-12
Tis the:
"Broadcom Corportation BCM4306 802.11b/g Wireless LAN Controller ( rev03 )"

@bailbath:  i will check your threads momentarily... but feel that I have already tried these only to be tarpitted

ketchup

---

### Post by iwizard on 2009-03-12
I've found this... 
"Simply install the package bcm43xx-fwcutter from your favorite package manager (synaptic, adept, or good ole apt-get or aptitude) and it will prompt you to download and install the firmware required for the Broadcom chipset. Once this install is complete, just reboot and the wireless chipset will connect without issue."

Sounds great... how do I "simply install the package bcm43xx-fwcutter"?  I keep getting package not found errors.

I love being a noob!  Normally everyone asks me stuff.  LOL.

ketchup

---

### Post by sonikamd on 2009-03-12
iwizard, I'm having almost exactly the same problem. One difference tho is my card is the bcm4318. I too have attempted several completely different how tos with no luck. One suggest a bcm43XX.intrepid.zip with both a manual and *.sh method. Another suggests using the ndiswrapper and the xp drivers. Another suggests removing/reinstalling the oem driver. I've failed on both a live usb of Ubuntu and a full installation, live usb of puppy linux and full install of SuSe.

From what I can tell the apt-get, bcm43xx methods both assume you have a working eth0 wired connection. No good in my case where wireless is the only option atm.

It seems the biggest roadblock atm is getting the card to turn on, most walk throughs end in "Your wireless LED should (blink/turn on/be turn-on-able [before/after reboot] etc)" where as mine just sits there dead. The card works in windows xp with no extra software.

If you find a solution please post back, as will I.

lspci reports: Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
Still part of the bcm43xx family.

---

