---
title: "locks up during boot"
date: 2008-05-16
forum: Hardware
---

### Post by miandy on 2008-05-16
I have a Gateway laptop model 600YGR that is approx. 4 yrs old.  It worked fine on the 6 series.  It was fine on 7.04.  There were a few problems with 7.10 that I hoped would be resolves with 8.04.  I just installed 8.04 and now the laptop starts out fine with no error messages that I can see during boot up but it gets to the brown log in screen with a clock in the center of the screen and just locks up.  I have tried numerous times and it wont boot up and always ends up in the same place.  I have always updated thru the web/Ubuntu updater.  I have not updated my desktop yet but my daughter has with no problems.  Thanks Mark.

---

### Post by hermes0710 on 2008-05-16
What is your graphics card and have you installed the driver through "Hardware Drivers" (If it's an ATI or ATI)? Can you post the contents of /var/log/Xorg.0.log?

---

### Post by miandy on 2008-05-17
Im sorry but I dont remember what graphics card is in it and I dont know how to ask it.    
 I would post the /var/log/Xorg.O.log but I do not know how to obtain it.  Thanks Mark

---

### Post by hermes0710 on 2008-05-17
At the point where it locks up pres ctrl+alt+F1 to turn in terminal mode. Login using your credentials and then execute:
```
cat /var/log/Xorg.0.log
```
and post the output here

---

