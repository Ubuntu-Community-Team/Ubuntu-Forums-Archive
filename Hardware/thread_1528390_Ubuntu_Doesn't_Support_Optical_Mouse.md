---
title: "Ubuntu Doesn't Support Optical Mouse?"
date: 2010-07-10
forum: Hardware
---

### Post by HDTimeshifter on 2010-07-10
I can't get my optical mouse to work with Ubuntu.  Below is my setup:

Ubuntu 10.0.4 LTS 64-Bit
ASUS P5Q Pro motherboard

GE WK3803 PS/2 optical mouse won't work.  No cursor movement when I boot up with this mouse plugged in.  Anybody with this mouse able to get it to work?

---

### Post by AltomineUK on 2010-07-10
That is weird... I don't think Ubuntu has got anything against optical mice. Type the following code to see if your mouse is ever recognised by the Filesystem. 

```
xinput list
```

these should show all the inputs (including your power, sleep buttons etc.)

---

