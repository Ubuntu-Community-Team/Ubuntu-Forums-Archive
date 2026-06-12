---
title: "power supply sufficient?"
date: 2010-04-15
forum: Hardware
---

### Post by KIAaze on 2010-04-15
Hi,

I've been having the following problem for a while now: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/514485](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/514485)

It seems power supply issues can also cause reboots, so I was wondering if my power supply is sufficient or stable enough.

My config:
- CPU: AMD Phenom X4 9750
- Graphic card: NVIDIA GeForce GTX 260
- Motherboard: Gigabyte GA-MA74GM-S2H
- RAM: 2x 2 GB DDR2 Stick
- HDD: 3.5" SATA 7200 rpm
- 1x DVD RW Drive
- 1 external fan (+ fan on CPU and probably some fan in the graphic card too)
- 8 USB slots (4 on motherboard, 4 in front) (mouse+keyboard over USB)
- Wireless: Edimax EW-7128g PCI Wi-Fi 54Mb

My current power supply:
Enermax Cyclops 500 W

Other:
Monitor+PC+speakers connected on one power strip connected to one power socket.

I tried [http://www.canardpc.com/cpc_apc/index.php](http://www.canardpc.com/cpc_apc/index.php) which recommended 450 W and [http://support.asus.com/PowerSupplyCalculator/PSCalculator.aspx](http://support.asus.com/PowerSupplyCalculator/PSCalculator.aspx) which suggested 650 W.

Is there a way to check if power problems caused the reboot in the logs or will I have to remove/replace some hardware to test it (which is cumbersome since it's a random problem)?

P.S.: When I use desktop effects, the screen sometimes becomes garbled or freezes completely. I read about some Nvidia driver issues, but could it be related to power issues too?

---

### Post by cascade9 on 2010-04-19
500 watts is fine for that system. 

> **KIAaze said:**
> Is there a way to check if power problems caused the reboot in the logs or will I have to remove/replace some hardware to test it (which is cumbersome since it's a random problem)?

P.S.: When I use desktop effects, the screen sometimes becomes garbled or freezes completely. I read about some Nvidia driver issues, but could it be related to power issues too?

Replacing hardware can sometimes help with finding power supply issues, but it can also give false positives. EG, yuo video card is dodgy, you remove it and put a smaller, less power hungry card in, it works fine..'a-ha!' you say, 'its a power supply issue'..you put a new power supply in, replace teh card, wham! issues again. 

If your screen becomes garbled, freezes or throws out artifacts, it could be a sick card, or it could be a heat issue. Try taking the side of the case, getting a esktop fan an blowign that into the case when you are using it. If the probably with the video card stop, its probabyl heat related. 

BTW, heat issues can also cause rebooting, etc, and could be the cause of your systems problems.

---

### Post by Sk41m4n on 2010-04-19
When it comes to PSU, W isn't the most important thing, what matters is how much ampere there's on the 12V rail(s). I don't know the specs for Enermax Cyclops 500W but you should look it up.

---

### Post by khelben1979 on 2010-04-19
If you intend to get a new power supply, I would recommend some reading: [DriverHeaven Power Supplies]("http://www.hardwareheaven.com/reviews.php?category=18").

A more powerful powersupply keeps down the noise and if it holds good quality you can have it for years to come... Corsair has done some real good ones.

---

