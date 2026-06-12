---
title: "Display brightness only 50% or 100%"
date: 2008-04-25
forum: Hardware
---

### Post by gutterballk7 on 2008-04-25
I am curious, has anyone else experienced a problem where their LCD brightness is only allowed to be roughly all the way down, all the way up, or in the middle? I get 100% and 50%. When I remove my power supply, my display will dim to 70%, as defined in the settings. And the display will dim to 30% when my mouse doesn't move. But I can't change it much by hand - only 100% and 50%.

I have a Dell E1505 - Hardy Heron.

Everything else is now working beautifully!

---

### Post by Potatoj316 on 2008-04-26
I have the same problem.  Dell inspiron E1505 and before hardy (gusty) I could adjust the brightness with Fn + up and Fn + down about 10% each press of the up/down button.  Now that still works but it is 50% up or 50% down each press of the up/down key.

---

### Post by acron1 on 2008-04-26
With my Thinkpad I have 8 levels of brightness using the Fn+Home/End keys.
I looked in "keyboard shortcuts" but I didn't find anything.

---

### Post by Potatoj316 on 2008-05-11
I used to have around 8 before I upgraded from 7.10 to 8.04, are there any other ways to control screen brightness

---

### Post by tcommbee on 2008-05-11
```
echo 2 > /sys/class/backlight/acpi_video0/brightness
```

should change the brightness to 20%. echoing the file should give the current setting. the acpi_video0 part might be different for you, but theres usually just one subdirectory. Changing the value obviously requires sudo and i dont know if out-of-bounds values can damage anything.

---

