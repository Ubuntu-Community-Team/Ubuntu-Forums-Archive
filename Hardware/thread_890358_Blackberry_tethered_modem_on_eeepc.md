---
title: "Blackberry tethered modem on eeepc"
date: 2008-08-15
forum: Hardware
---

### Post by GoldNugget on 2008-08-15
I just got a new Blackberry Curve and would like to use it as a tethered modem on my eeepc running Gutsy. 
Running wvdialconf gives an error stating that no modem is detected.
Some websites suggest installing Barry from Sourceforge, however that looks like a program to sync the blackberry, not use it as a modem.
There is a program called vzaccess which is available for Windows or Mac from Verizon which I probably need. I found an unsupported .rpm package and rumours of a .deb package but have been unable to find it, despite hours of googling. 
There are some how-to websites out there, but most are very complicated and very out of date. A friend is running Suse and said it installed and runs flawlessly for him. 
Any suggestions? 
Thanks in advance.

Edit: I have installed Berry and gnome-ppp, unfortunately the modem is still not detected.

---

### Post by GoldNugget on 2008-08-15
Another update: I converted the vzaccess .rpm file to .deb. It seemed to install fine. There is a menu item for it, but when selected it seems to do nothing. The modem is still not recognized.

---

### Post by blazercist on 2008-09-01
I have the same phone and want to use it with bluetooth on an msi wind if you have any news regarding this please let me know.


Here's what I know:
AFAIK, barry doesnt have support for the verizon curve pci id, some digging tells me that support was supposed to be in the next barry update which never came.  This is probably a very easy fix if you can sniff the usb logs in windows and find the pci id and then modify the barry source, however, I don't have windows and on a scale of 1-10 im probably a -99 when it comes to programing.

Barry would theoretically allow for tethering with the BB, the problem is that the BB isnt natively recognized by ubuntu, barry provides a layer that allows the BB to be recognized properly and once that is done you can probably use the normal wvdial method as with any other cell phone.

I once got my BB worldphone to be recognized properly with barry on ubuntu however it was buggy and unreliable... It was a while ago so I dont know if there have been any improvements in barry.


The BB is a pretty universal device for business people and smart phone people in general I'm somewhat dissapointed in the lack of linux support for BB's in general.. I kno its not a linux problem its a BB problem but hey burning the candle from both ends usually makes it burn faster :)

also, the vzaccess program is worthless.


I did a little reading and apparently you don't need any third party packages to get it working using bluetooth so perhaps this is the way to go, I haven't tested it yet perhaps if I have some free time I will report back with my results

---

### Post by jasonbrisbane on 2008-09-09
Hi,

I'm trying the same think but on a Dell 1400.

There are sources for XmBlackberry and a few websites (search the forums too!) detailsing how to get it going, but I have an 8800 that fall sover as the Serial port isnt found when xmblackberry searches the device!

(It is supposed to recognise and show you the virtual port it is assigned to (i.e. /dev/ttyp/1 or something like that. Mine come sup with No Serial Port found.)

Post hear if you find something!

---

