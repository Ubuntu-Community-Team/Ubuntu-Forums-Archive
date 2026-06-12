---
title: "Touch screen issues"
date: 2019-10-21
forum: Hardware
---

### Post by abishur on 2019-10-21
I'm using Ubuntu 19.10.  I have a touchscreen I'm using that is listed as “Renesas Electronics USB Touch (Win8)” when I type in ```
xinput list
```

My issue is that it doesn't seem to be processing mouse release events correctly in certain situations.  For instance if I open the file manager and click on any menu it will not allow me to select any option from that menu.  So it recognizes that I clicked on the "file" menu, but then I can't select "exit" or anything else under the menu.

It also won't work with a Java program I have.  When I select a button it will change colors when pressed denoting it sees I have clicked it, but then when I release it nothing happens.

I have tried some basic troubleshooting.  Using xinput test with a mouse shows a RawButtonPress and a RawButtonRelease event but with the touch screen I get:

```

EVENT type 22 (RawTouchBegin)
   Device: 10 (10)
   detail: 10
   valuators:
      0:38067.66 (38067.66)
      1:22994.68 (2294.68)

EVENT type 24 (RawTouchEnd)
   Device: 10 (10)
   detail: 10
   valuators:
      0:38067.66 (38067.66)
      1:22994.68 (2294.68)
```


Using ```
xev -event mouse
``` with a mouse and clicking gives me:
```

ButtonPress event, serial 25, synthetic NO, window 0x1c00001,
    root 0x103, subw 0x1c00002, time 4111605, (42,48), root:(700,375),
    state 0x10, button 1, same_screen YES
    
ButtonRelease event, serial 25, synthetic NO, window 0x1c00001,
    root 0x103, subw 0x1c00002, time 4112907, (42,48), root:(700,375),
    state 0x110, button 1, same_screen YES 
```


And with the touchscreen and touching gives me:


```

ButtonPress event, serial 25, synthetic NO, window 0x1c00001,
    root 0x103, subw 0x1c00002, time 4190526, (42,37), root:(465,331),
    state 0x10, button 1, same_screen YES
    
ButtonRelease event, serial 25, synthetic NO, window 0x1c00001,
    root 0x103, subw 0x1c00002, time 4190663, (42,37), root:(465,331),
    state 0x110, button 1, same_screen YES    
```


Any ideas what could be going on to give me this weird behavior?  There are definitely very specific clicks that are ignored when using the touchscreen for some reason.

---

### Post by abishur on 2019-11-05
Anyone have any ideas on what's going on with this touchscreen?  Or how I could find out what drivers its using?  Maybe if I can look through the driver file I can find what's going on with the release event.

---

### Post by jimmyrus on 2019-11-07
There's a version of ubuntu specifically for touch devices that might be worth a try   [https://ubports.com/](https://ubports.com/)

---

