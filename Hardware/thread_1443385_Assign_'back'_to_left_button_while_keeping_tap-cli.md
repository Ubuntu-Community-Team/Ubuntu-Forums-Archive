---
title: "Assign 'back' to left button while keeping tap-click on trackpad?"
date: 2010-03-31
forum: Hardware
---

### Post by floepie on 2010-03-31
In Windows on the laptop, I am accustomed to assigning the left mouse button to the 'back' command (used mainly in the browser and explorer) while maintaining the tap-to-select on the trackpad itself.  Using xinput, I can reverse the 'left-click' and 'back' commands using the following where 11 is the device ID:
```
xinput set-button-map 11 8 2 3 4 5 6 7 1 9 10 11 12
```

However, both tap-to-left-click and the left button are mapped to 'back'.  Is there a way to separate the two?

---

