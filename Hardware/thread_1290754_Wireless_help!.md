---
title: "Wireless help!"
date: 2009-10-13
forum: Hardware
---

### Post by Kevin1790 on 2009-10-13
This is my first post, I recently installed ubuntu 9.04 on my dell inspiron b130. I have the 1370 WLAN MiniPCI card and I can't access the internet. Could someone tell me where to start?

Thanks

---

### Post by RaveJunkie on 2009-10-13
I have 9.04 on my netbook and i use a wireless via the "restricted drivers" option  system>admin>restricted drivers   then i got the file it wants from the manufacture (dell for me) then you get the file *cant remember right now but its like a .inf* then use the app "ndiswrapper" to install it. 

that is IF thats even all needed, have you checked if your card is supported via the kernal?

if so you can just use the network tool like you would in winblows

---

### Post by Kevin1790 on 2009-10-14
yeah the file is bcmwl5.inf, i have that; but under the hardware/restricted drivers i can't get the broadcom B43 wireless driver to activate

---

### Post by admelfo on 2009-10-14
Have you tried installing madwifi??

---

### Post by mocoloco on 2009-10-15
To install using ndiswrapper just install the graphical tool called [ndisgtk]("apt:ndisgtk") (click that link to download it via your software sources).

Then open System -> Administration -> Windows Wireless Drivers.  It will have you browser to where your inf is installed, and that should be it.

---

### Post by Kevin1790 on 2009-10-15
Ok it's shows the inf bcmwl5 as a currently installed windows driver, but it says there is no hardware present and when I click on configure network it says could not find a network configuration tool

---

### Post by Kevin1790 on 2009-10-16
My wireless card is the Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

---

### Post by mocoloco on 2009-10-16
> **Kevin1790 said:**
> yeah the file is bcmwl5.inf, i have that; but under the hardware/restricted drivers i can't get the broadcom B43 wireless driver to activate

Wait I missed this part.  If you have a driver showing up under the "Hardware Drivers" tool you should use it.  Why can't it activate, what error does it give you?
Did some searching, according to [this page]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM43xx_%28all%2C_ndiswrapper/firmware%29") it should be a better option and ndiswrapper for most people.

Make sure to disable (remove) the ndiswrapper driver before you try it again.

---

### Post by Kevin1790 on 2009-10-16
I'm not sure why; when i click activate for the Broadcom B43 wireless driver it still says the driver is not activated, no error pops up

---

### Post by mocoloco on 2009-10-16
OK. First of all again make sure you've removed the windows driver for now.  Then open System > Administration > Software Sources.  Under the first tab, make sure "Proprietary drivers" is enabled (in fact you probably want all but "Source code" enabled).

When you open "Hardware Drivers" and click activate, it should ask for your password, and should download something.  If after doing that it still doesn't show as active you may need to reboot for it to activate.

If you're really not getting anything when you click active, then take a screenshot of the hardware drivers app, with it open just go to Applications > Accessories > Take a screenshot.  Set it to get the active window in 3 seconds, it will prompt you to save the file in .png format.  Post that screenshot here.

---

