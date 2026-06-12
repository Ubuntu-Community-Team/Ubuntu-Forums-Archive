---
title: "Laptop Sound"
date: 2007-07-21
forum: Hardware &amp; Laptops
---

### Post by File13 on 2007-07-21
I saw an open thread about this but it wasnt answered from back in 2006, im having some problems with my laptop sound. When i plug in my head seat to talk on Ventrilo the sound comes from both the laptop speakers and the headphones. Also people on Ventrilo claim that the voice is somewhat low so im wondering where i can go to change that in the Ubuntu sound instead of the Ventrilo setup.

---

### Post by scrooge_74 on 2007-07-21
did you check in the alsamixer (type it on a terminal) there is a jack sensor for the headphones. On mine the headphone would not work until i put it on automatic

---

### Post by File13 on 2007-07-21
ext mic and int mic are both set at 0, i dont see how to change them though.

---

### Post by scrooge_74 on 2007-07-21
when you type alsamixer on the terminal it show a lot of things under the headphone if you move the arrows to get under the bar you will see on top it says jack sense [off] if you press the "m" key it shoud change to on or auto

---

### Post by File13 on 2007-07-21
well i dont hear any sound now, and now i cant hear people in ventrilo but they can hear me.

---

### Post by File13 on 2007-07-22
bump

---

### Post by ugm6hr on 2007-07-22
Probably best to type ```
alsamixer
```

Then do a screenshot so we can see what settings you have.

If you can't do a screenshot, post the output from ```
amixer
```

---

### Post by File13 on 2007-07-22
what i did was followed the steps i found on another thread for sound problems which basically uninstalled and reinstalled the drivers, but now when i play games or music i hear clicks and pops.

---

