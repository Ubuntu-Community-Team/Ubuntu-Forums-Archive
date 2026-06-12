---
title: "Switching to an external monitor from laptop monitor"
date: 2007-11-15
forum: Hardware &amp; Laptops
---

### Post by d1ss0nant on 2007-11-15
Hi - I run gutsy gibbon 64 bit edition on my compaq r3000z laptop.  It runs fine when i'm using my laptop screen, and my external monitor runs fine when I boot up with it attached - but if I want to toggle between laptop monitor and external monitor, I'm unable to do so.  If I were using windows  I would use the fn+f4 shortcut and I was in business - now, I am either forced to restart or I can do it by killing xorg ( [http://ubuntuforums.org/showthread.php?t=555492](http://ubuntuforums.org/showthread.php?t=555492) )  Is there a better way?  A way to do it without logging myself off?  Thanks

---

### Post by Syke on 2007-11-15
You can try xrandr to turn it on and off:

On (replace the resolution with the one you want):
```
xrandr --output VGA --mode 1024x768
```

Off:
```
xrandr --output VGA --off
```

---

### Post by d1ss0nant on 2007-11-18
unfortunately, this did not work for me :(

---

### Post by Jeezus on 2008-01-25
I'm really glad to learn about this xrandr command... It's making things easier for me. =)

---

