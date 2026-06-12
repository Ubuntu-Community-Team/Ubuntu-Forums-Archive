---
title: "Logitech M310 strange behavior"
date: 2011-04-05
forum: Hardware
---

### Post by mcovey on 2011-04-05
This is a wireless mouse with a mini receiver not bluetooth, I have used this mouse before with xubuntu installed on a mac and it worked out of the box. I am now using Lubuntu 10.10 on a Dell Mini 9.

The problem is that the mouse works only when the laser light is on, then stops. I installed both logitech-applet and lomoco. Both of them solve the problem for 5 seconds. If I type lomoco -s I can see the mouse as "unsupported logitech device: unknown" and it works. If I keep moving it, it keeps moving. If I let it stay still for long enough that the light goes out, it stops working. The same thing happens when I type logitech_applet - it works, then after I stop moving it, stops.

I just tested it and it seems that if I fail to move it in the first place shortly after typing either lomoco or logitech_applet, it will time out somehow and never move to begin with.

Just tested something else and if I reboot the computer, I don't have to type anything, it works for a moment after X loads, then stops working.

Any ideas?? Thanks.

Edit: just to confirm, I've been over all the basics. Its working on Windows, fresh battery, laptop plugged in to power, tried rebooting, checked gconf settings for power manager and such.

edit again:
Typing usb-devices in console shows:
Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#= 1 Spd=12 MxCh= 0
Ver= 2.00 C1s=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs= 1
Vendor=-46d ProdID=c52f Rev=22.00
Manufacturer=Logitech
Product=USB Receiver
#Ifs= 2 Cfg#= 1 Atr=a0 MxPwr=98mA
If#= 0 Alt= 0 #EPs= 1 C1s=03(HID ) Sub=01 Prot=02 Driver=usbhid
If#= 1 Alt= 0 #EPs= 1 C1s=03(HID ) Sub=00 Prot=00 Driver=usbhid

---

### Post by girishadat on 2011-11-07
Can you confirm if the problem still persists? Or were you able to find any solution for the problem? I am planning to buy this mice... Got attracted by the 12 months battery life and seems to be of great Value For Money!

:icon_frown:

---

### Post by Rodney9 on 2011-11-08
My logitech M305 wireless mouse in Lubuntu 11.10 works perfectly out of the box.

Rodney

---

### Post by girishadat on 2011-11-08
Thanks Rodney9. :)

I tried comparing the mices - M310 and M305. Just saw a difference of Laser and battery life.

310 - Laser(is this the problem for first post in this thread?), 12 months battery life.
305 - high definition optical tracking, 5 months battery life.

And both at same price. Anyway I am going for 310 and see what my luck is. :)

---

### Post by HandeH on 2011-12-24
Logitech M310 works out of the box in Lucid Lynx. Details of the mouse from lsusb are: ID 046d:c52f Logitech, Inc. 
:D

---

### Post by girishadat on 2011-12-24
I bought M310 and have been working out of the box like a charm for past a month! Its a perfect piece of technology. And I'm in 11.10 Oneiric Ocelot!

---

