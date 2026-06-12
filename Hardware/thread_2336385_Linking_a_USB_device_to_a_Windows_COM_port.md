---
title: "Linking a USB device to a Windows COM port"
date: 2016-09-07
forum: Hardware
---

### Post by nelmo2 on 2016-09-07
I am trying to run a Windows-based program (under wine v1.8) which reads from a USB device. I can see the USB device:

```
$ lsusb |grep 340
Bus 004 Device 004: ID 1a86:7523 QinHeng Electronics HL-340 USB-Serial adapter
```

...and I've run the driver setup program which said it was successful. However, in the Windows program, it asks me to select the USB device and only offers a drop-down of windows-style COM ports (COM1 to COM9). 

I've tried all of them but none work - any idea how to associate the 2?

---

### Post by nelmo2 on 2016-09-08
If it helps anyone else,  I found this:

[http://r.duckduckgo.com/l/?kh=-1&uddg=http%3A%2F%2Fg8ogj.org%2Ffiles%2FUsing%2520USB%2520serial%2520ports%2520under%2520wine%2520howwto%2520ipb.pdf](http://r.duckduckgo.com/l/?kh=-1&uddg=http%3A%2F%2Fg8ogj.org%2Ffiles%2FUsing%2520USB%2520serial%2520ports%2520under%2520wine%2520howwto%2520ipb.pdf)

Haven't confirmed it works yet but looks promising so far...

---

