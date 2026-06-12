---
title: "gold usb phone - howto make buttons work?"
date: 2007-07-27
forum: Hardware &amp; Laptops
---

### Post by suoko on 2007-07-27
Hi,

I just bought an usb phone to use it with skype.
I'm trying it with dapper and audio in/out are perfectly working.
Hoever I'd like its buttons (the dial and hand up ones, I don't care about the keypad ones) to work.
How can I check if they send some kind of signal to the PC? I tried with the keyboard shortcuts under gnome preferences to see if I could associate an action to the phone buttos, but they're not recognized.
Any hints?
It would be nice to have them working in order to easily answer the phone.
To call it's better to use the pc software anyway....

---

### Post by geraldm on 2007-07-27
Please post the results of ```

cat /proc/bus/usb/devices

``` trimmed for just this device.  That should give the clues.
Gerald

---

### Post by suoko on 2007-08-22
here it is:

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0c45 ProdID=184c Rev= 1.00
S:  Manufacturer=GENERIC
S:  Product=USB Audio Device
C:* #Ifs= 4 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 0 Cls=01(audio) Sub=01 Prot=00 Driver=snd-usb-audio
I:  If#= 1 Alt= 0 #EPs= 0 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
I:  If#= 1 Alt= 1 #EPs= 1 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
E:  Ad=01(O) Atr=09(Isoc) MxPS= 200 Ivl=1ms
I:  If#= 2 Alt= 0 #EPs= 0 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
I:  If#= 2 Alt= 1 #EPs= 1 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
E:  Ad=82(I) Atr=05(Isoc) MxPS= 200 Ivl=1ms
I:  If#= 3 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid
E:  Ad=83(I) Atr=03(Int.) MxPS=   7 Ivl=10ms

while lsusb reports this:
Bus 002 Device 003: ID 0c45:184c Microdia

Link to phone manufacturer: [http://www.skypephoneusb.com/index.html](http://www.skypephoneusb.com/index.html)

---

