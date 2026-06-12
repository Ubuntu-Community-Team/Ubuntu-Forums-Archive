---
title: "Logitech YRH35 Alternate F-Keys"
date: 2010-01-12
forum: Hardware
---

### Post by Amagineer on 2010-01-12
I have [THIS](http://www.kpsurplus.com/img/full/8bfee1753f40303872b775bee721a303897620f2.JPG) keyboard and want to get the alternate function keys working. To activate them one disables the "F-Lock" and the alternate functions become available (See all those pretty pictures on top of the F-Keys?).

I ran xev and pressed said keys without F-Lock being on (As F-Lock enables normal F-Key functionality) and got no output as a result thereof. I would love to get these keys working, and once I get them sending something mapping them to media keys and the like should be trivial.

UPDATE: Even ```
cat /dev/input/by-id/usb-Logitech_USB_Receiver-event-kbd
``` won't output when I press the magic secondary F keys (Although the real F-Keys work fine)

---

