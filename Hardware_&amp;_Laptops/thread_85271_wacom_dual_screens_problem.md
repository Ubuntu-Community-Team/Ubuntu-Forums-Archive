---
title: "wacom dual screens problem"
date: 2005-11-02
forum: Hardware &amp; Laptops
---

### Post by oly on 2005-11-02
hi, 

is there anyway to limit the area your pen can move on, or set the visible size with a wacom.
i have dual screens and it has trouble figuring out where i can move the mouse pointer two, the area is smaller than the screen.

i need away of either setting it to just the first monitor or the full size of both, only actually need it for first monitor though as thats the larger one.

anyideas on how and if it can be done ??

---

### Post by 23meg on 2005-11-02
You can use the xsetwacom command (found in the package wacom-tools) to do this. Type "xsetwacom list param" to see a list of parameters you can issue.

---

### Post by oly on 2005-11-02
thanks for that info, i take it i use TopX TopY BottomX and BottomY, but what is a tablet unit and how do i map it to my screen.

either 1280x1024 or 2304x1024 as i guess using those values would not work as there pixels not tablet units.

---

### Post by 23meg on 2005-11-02
For most wacom tablets one tablet unit is 1/1000 inch. You should run the wacdump utility (which also comes in the wacom-tools package) to determine coordinates for the area to which you want to limit movement, and enter those as xsetwacom parameters.

---

