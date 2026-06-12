---
title: "Toshiba Satellite U920T - touch screen not working with Ubuntu  14.04"
date: 2014-10-16
forum: Hardware
---

### Post by Nostronna on 2014-10-16
Hello Everybody,
I have a toshiba Satellite U920T, less than one year old, that has a touch screen.
When I bought it I immediately install Ubuntu 12.04 and everything worked very well, included the touch screen. Recently the touch screen stopped working with no apparent reason and without any error message. I'm not sure if this happened after an update or not.
I've done all the possible updates, but I had no improvement. 
I've tried with the "calibrate touchscreen" app but I have a message on the terminal saying "Error: No calibratable devices found"
I've upgraded to Ubuntu 14.04 but still no improvement, the touch screen is still not working.
I've tried to search for additional drivers but it says "no additional drivers available".
....Any suggestion???
do I have to think it is an hardware problem? it seems strange...
help please!!

Thank you,
Michela

---

### Post by Vladlenin5000 on 2014-10-16
An hardware problem is a possibility indeed but we shouldn't jump to that conclusion before some troubleshooting.
I suggest you test it in a live session. Try the current 14.04 first and if it works then most probably some update broke the touchscreen support. If it doesn't work in a 14.04 live session but work on a 12.04 one, then we have a regression somewhere (we'll see about properly reporting it to the developers later). If it doesn't work in 12.04 then it probably is an hardware issue.

---

