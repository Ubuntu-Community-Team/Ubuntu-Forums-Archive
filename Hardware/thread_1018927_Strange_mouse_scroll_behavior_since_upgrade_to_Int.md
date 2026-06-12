---
title: "Strange mouse scroll behavior since upgrade to Intrepid Logitech MX700"
date: 2008-12-22
forum: Hardware
---

### Post by perenti on 2008-12-22
Since I upgraded to Intrepid my Logitech MX700 (MX-700) mouse is acting strange. When I use the mouse wheel to scroll vertically I also scroll horizontally. I tried several things and searched this forum all over, however to no avail. My current fdi is:

```
 <match key="info.capabilities" contains="input.mouse">
     <merge key="input.x11_options.ButtonMapping" type="string">1 2 3 4 5 6 7 8 9 10</merge>
     <merge key="input.x11_options.YAxisMapping" type="string">4 5</merge>
     <merge key="input.x11_options.EmulateWheel" type="string">true</merge>
     <merge key="input.x11_options.Buttons" type="string">10</merge>
     <merge key="input.x11_options.Emulate3Buttons" type="string">true</merge>
   </match>

```

I hope someone rescues me from diagonal scrolling hell... :confused:

---

