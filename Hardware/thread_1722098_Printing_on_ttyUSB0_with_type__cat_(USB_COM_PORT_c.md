---
title: "Printing on ttyUSB0 with type / cat (USB COM PORT converter)"
date: 2011-04-05
forum: Hardware
---

### Post by ameximes on 2011-04-05
Hi everyone,
I have a laptop which have not a com or lpt port on that and I need to use one of them in order to design stickers with Argox Label printer.

In Windows world i use
```
type test.txt > lpt1
```command to send my PPLA formated text over lpt to the printer but now I have no lpt port and don't interest in Windows and i have a USB <-> COM converter.

I guess equal command is
```
cat test > /dev/lpt 
```When i plug my converter into USB port then 
```
 dmesg | tail -n 50
```I see => usb 8-1: pl2303 converter now attached to ttyUSB0

then I try 
```
cat test > /dev/ttyUSB0
```or
```
cat test > /dev/ttyUSB0 9600
```nothing happens... console creating a new line (on screen) than blinking cursor.

Any suggestions?

---

