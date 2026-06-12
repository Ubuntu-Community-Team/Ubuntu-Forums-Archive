---
title: "Scripting with a USB modem"
date: 2013-05-16
forum: Hardware
---

### Post by ubuntologist on 2013-05-16
Hi there,

I am writing a bash script that issues a Hayes command (AT!SCACT?1) & then uses the response from the usb modem (/dev/ttyUSB2).

```
echo -e AT\!SCACT\?1 "\r" > /dev/ttyUSB2 && cat /dev/ttyUSB2
```

Unfortunately, I have to manually break as ttyUSB2 remains open. 

I am limited in that the solution can only use utilities available on a standard Ubuntu server installation.

Any help would be appreciated as I'm sure there must be a more elegant solution. 

Cheers.

---

### Post by steeldriver on 2013-05-16
maybe you could use a chat script? or expect?

---

### Post by ubuntologist on 2013-05-17
I will look into chat but it doesn't look like expect comes with a standard install.

Thanks steeldriver.

---

### Post by steeldriver on 2013-05-17
Yes I think you're right - expect is optional, but if you have ppp you should have chat

However I haven't used it since the days of trying to get an old Sun connected via dialup

---

### Post by ubuntologist on 2013-05-18
Thanks - looks like chat is the way to go!

---

