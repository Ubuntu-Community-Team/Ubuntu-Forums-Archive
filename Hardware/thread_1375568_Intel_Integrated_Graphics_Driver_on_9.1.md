---
title: "Intel Integrated Graphics Driver on 9.1"
date: 2010-01-08
forum: Hardware
---

### Post by terrapin893 on 2010-01-08
Just installed 9.1 today, my first Linux machine.  

The comp is a Dell Dimension 2400 and Im trying to get the video driver to work to get a better screen resolution.  

00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

When I go to Hardware Drivers, it lists "No Proprietary Drivers are in Use on this System" 

Did some googling and found this link from Intel with some files.  Im not opposed to spending whatever time is necessary doing what needs to be done and learning the ropes, but as of right now I have poor screen resolution and it doesnt appear that the machine is picking up on my monitor.  

[http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=8203&ProdId=865&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=8203&ProdId=865&lang=eng)

Any nudge in the right direction would be much appreciated.  

Thanks!

---

### Post by nick_goodfate on 2010-01-08
check this : [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
it detects your card and suggest you the best driver.

---

### Post by coffeecat on 2010-01-08
> **nick_goodfate said:**
> check this : [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
it detects your card and suggest you the best driver.

From that link:

> only ATI and Nvidia cards are supportedThis is not going to help the OP.

---

### Post by terrapin893 on 2010-01-08
Yes, it is not a card but an integrated chip on the board.  Intel 82845G.  

Any other ideas?

---

### Post by coffeecat on 2010-01-08
@terrapin893, I'm sorry I didn't add anything constructive for you. That's a very old Intel graphics chipset and a quick google threw up a number of other people with similar problems with that chipset. I had a machine with the 845G Intel graphics when I first started using Linux in 2005. Graphics performance wasn't brilliant but I could get usable resolution. But since then, there have been many changes in the Intel graphics driver. Perhaps the older chipsets have been neglected - I don't know.

If no one posts anything helpful, the only thing I can suggest is to buy a graphics card for that machine. Unfortunately, you're a bit limited. Googling reveals that your machine has only PCI slots - no AGP (and obviously no PCIe). Is that correct? Which might make finding a card difficult - or even impossible. If you can find a supplier of PCI graphics cards, choose Nvidia, not ATI. Choose something in the Geforce 6*** or 7*** range and you should be fine. They will run on the open source 'nv' driver that comes with a default install, and the proprietary 'nvidia' driver (which will give you 3d acceleration) will appear in the Hardware Drivers utility.

---

### Post by terrapin893 on 2010-01-08
Ah, there we go an answer!  

First, thank you.  Yes, it is an old computer with an old integrated graphics chip.  I bought the computer for $5 from a company that was going out of business.  I can see and I can do things, so all is not lost.  And you are correct, it has merely a PCI slot, no PCIe or AGP.  I will see what I can do about getting a new card, if I can.  Knowing is half the battle.

---

### Post by terrapin893 on 2010-01-08
Update: 

Trying to run the install.sh from the Intel driver download package leads me here: 

[: 1361: 0: unexpected operator
[: 1361: unexpected operator

Compiling DRM module...install.sh: 1361: Syntax error: Bad fd number

Im too tired to look further into it right now.

---

