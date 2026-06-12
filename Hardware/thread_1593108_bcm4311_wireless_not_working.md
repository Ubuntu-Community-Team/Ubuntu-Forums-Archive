---
title: "bcm4311 wireless not working"
date: 2010-10-11
forum: Hardware
---

### Post by Andrew Golightly on 2010-10-11
Just installed Maverick on a friends old laptop.

Wireless firmware is not being installed. His wireless card is a broadcom bcm4311.

I've read [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx) but going into Synaptic, the bcmwl-kernel-source module doesn't seem to be there. Looking in my Synaptic Package Manager, I see the module though (I'm still using Lucid).

As the computer is booting, I see this error message:

> Oct 11 21:47:17 frano kernel: [   16.518321] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
Oct 11 21:47:17 frano kernel: [   16.518409] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
Oct 11 21:47:17 frano kernel: [   16.518485] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.

What to do???

thanks,
Andrew

---

### Post by IcarusR on 2010-10-11
Have you read the linked web page in the error ?? Have you tried the instruction there ?

Install Lucid ??

There will undoubtedly be teething problems / bugs with Maverick for the next couple of months.

Personally I never install any new OS till it has been out for a few months for this reason.

---

### Post by snafu006 on 2010-10-11
With that wireless card you need to first get that updates do to that just connect the ethernet cord in to the computer from the modem or router . now if you stealing internet and you have a MAC computer just plug in the ethernet cord from the MAC computer to the ubuntu computer and share the connection worked for me a long time ago lol.

---

### Post by Andrew Golightly on 2010-10-11
I ended up inserting the Lucid disk... reloading Synaptic so that it read packages from there too... then installed a couple of b43* packages.

Got it all working now. Thanks.

---

