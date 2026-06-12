---
title: "what driver for the hercules dualpix hd webcam?"
date: 2009-02-07
forum: Hardware
---

### Post by manu-tm on 2009-02-07
Hi!

I'm trying to get my Hercules Dualpix HD webcam work in Ubuntu.

I modprobed ov534 and the webcam is recognized but it's still not working. I had /dev/video0 but dmesg output says the driver uses video device -1. So I was not sure if the ov534 driver was the right one or if there were a better choice (if any.)
After reading that the Dualpix Exchange is uvc compatible (the hercules company guys said that) I tried with uvcvideo. But nothing again.
Then I checked on [www.linux-usb.org](www.linux-usb.org). My cam is a Dualpix *HD* (06f8:3003), not *Exchange* (06f8:3005.)

If somebody uses the same cam or have suggestions, please let me know.

Many thanks in advance.

---

### Post by manu-tm on 2009-02-11
I e-mailed people at Hercules and they said: reference sensor ov9655.
Which is very informative indeed. Too bad I don't have a degree in electronics.
So if somebody know something on the subject, please don't hesitate to let me know. Thank you.

---

