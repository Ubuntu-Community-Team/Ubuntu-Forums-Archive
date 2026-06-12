---
title: "conky battery life bar?"
date: 2008-10-12
forum: General Help
---

### Post by danbuter on 2008-10-12
I have the following line in my conky file:

${color red}battery: ${color red} $acpiadaptor, ${battery_percent BAT1}%

This works great. However, I'd like to add in a battery life bar beneath this line that would look similar to the swapbar, etc. Is there a way to do this? Thanks!

---

### Post by OutOfReach on 2008-10-12
Try this variable:
```
${battery_bar}
```

EDIT: Wait are you talking about the actual life of the battery, or how much time is left until the battery discharges?

---

### Post by danbuter on 2008-10-12
The bar outline would indicate the 100% battery life, while the "moving fill" would indicate actual battery life remaining. If this possible, it would be very helpful for me.

---

