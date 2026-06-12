---
title: "Aspire One Netbook - Random Paste of Buffer"
date: 2009-07-02
forum: Hardware
---

### Post by jbeiter on 2009-07-02
This is getting really annoying and I'm not sure where it is coming from. I'm pretty happy with this Aspire One on Jaunty but when I am typing, random crap will get pasted in to what seems to be random sections of what I am typing. Happened twice while I was typing this posting. I'm not hitting anything but keys and I'm not anywhere near the touchpad's "button" though I may be near the touch pad.

Anyone hear of this or know where it is coming from? It is annoying as hell!

---

### Post by jbeiter on 2009-07-03
bump...   does anyone know of a way to turn off the touch pad?

Nothing in BIOs but perhaps there is a software way to do it?

---

### Post by snakeman21 on 2009-07-03
I had this problem too, and it's an easy fix. It happens because the touchpad is so sensitive that when you're typing, if you touch it in any way, you will begin typing wherever the cursor is.  This can fixed by opening going to preferences and selecting Sessions.  Click the "add" button and add the following:

```
Name: Syndaemon
Command: syndaemon -d -t -i 1
Description: Disable touchpad whilst typing
```

In the command box, you can replace 1 with any number.  The number represents how many seconds the touchpad will be disabled for after each keystroke.  1 second has worked perfectly for me.

---

### Post by jbeiter on 2009-07-04
Thank you!  BTW, anyone trying to do this on Jaunty, "sessions" has been replaced by "startup applications".

---

### Post by snakeman21 on 2009-07-04
No problem!  Trust me, I know how annoying that is!

---

### Post by joshedmonds on 2009-07-08
FYI my AA1 has a Fn-F7 touchpad switch

---

### Post by snakeman21 on 2009-07-08
Yes, but nobody wants to keep switching it on and off every time they need to type something.

---

