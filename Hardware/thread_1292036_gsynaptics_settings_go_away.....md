---
title: "gsynaptics settings go away...."
date: 2009-10-15
forum: Hardware
---

### Post by roxy.pda on 2009-10-15
Is there any way to make the gsynaptics settings stick? every time I restart my laptop I have to run gsynaptics to set sensitivity and remove scrolling again.... Kind of a pain....

Roxy

---

### Post by kerry_s on 2009-10-15
add-> **gsynaptics-init --sm-disable**
to the startup

---

### Post by roxy.pda on 2009-10-15
Thanks! That did the trick!

Roxy

---

### Post by roxy.pda on 2009-10-16
BTW, where  does Gsynaptics store the settings? 

Thanks,
Roxy

---

### Post by kerry_s on 2009-10-16
**man gsynaptics**

---

### Post by roxy.pda on 2009-10-16
Doh!! Feeling kinda stupid....  But still loving xubuntu on my eee pc!

Thanks Kerry!

---

### Post by roxy.pda on 2009-10-19
setting Gsynapticsto the lowest sensitivity level is not low enough... It's really annoying on web pages....
Looking at the %gconf.xml file is a bit confusing, I see a sensitivity "value" of "0" when set to the lowest level and "4" when set to the highest, there is also a long number for "mtime", can that be edited to further lower sensitivity?
here is my current setting:
<entry name="sensitivity" mtime="1255967463" type="int" value="0"/>

---

