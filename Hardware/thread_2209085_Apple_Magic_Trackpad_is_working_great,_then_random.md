---
title: "Apple Magic Trackpad is working great, then randomly stops until hciconfig reset"
date: 2014-03-03
forum: Hardware
---

### Post by cgcuriouscg on 2014-03-03
I paired a Apple Magic Trackpad with my laptop through the kde bluetooth system. It works fine until I touch it with too many fingers or swipe it too much resembling some sort of a gesture (or until the computer goes to sleep), then it simply stops ignoring any input, after performing 
```

sudo hciconfig hci0 reset

```
it is automatically reconnected and works again, for a while ...


The same problem exists when connecting it from the commandline using 
```

 sudo hidd --connect
```

with evtest I found out that the problem is when a tripletap or quadtip is detected the event gets retriggered a gazillion times, this is one single three finger tap: 
[http://pastebin.com/KWYHbx5G](http://pastebin.com/KWYHbx5G)


[LIST=1]
[*][COLOR=#000000]

Event: time 1393907073.611256, -------------- SYN_REPORT ------------[/COLOR]
[*][COLOR=#000000]Event: time 1393907073.647294, type 1 (EV_KEY), code 334 (BTN_TOOL_TRIPLETAP), value 2[/COLOR]
[/LIST]

If I turn the trackpad off the events still keep firing, not sure if it is stuck in the event queue or if it is getting retriggered in the bluetooth stack ..

---

