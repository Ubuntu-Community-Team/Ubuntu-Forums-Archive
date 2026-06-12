---
title: "How do you turn off edge scrolling?"
date: 2010-11-04
forum: Hardware
---

### Post by or3gano on 2010-11-04
Every time i work on my laptop i start scrolling like crazy. I can't figure out how to turn off the scrolling/tacking on my mouse pad and it has already cost me several mistakes. Can someone tell me how to do this?

---

### Post by IcarusR on 2010-11-04
To see the current settings for touchpad in a terminal run

```
synclient -l
```

All these settings can be changed using synclient.

See the synclient manual for how to use synclient

```
man synclient
```

To turn off HorizEdgeScroll

```
synclient  HorizEdgeScroll=0
```

1 = set
0 = not set

---

### Post by Manyette on 2010-11-04
Or try Preferences->Mouse->Touchpad->Scrolling

---

### Post by or3gano on 2010-11-05
When I try synclient  HorizEdgeScroll=0 It displays this message:
Couldn't find synaptics properties. No synaptics driver loaded?
My mouse preferences don't have any options for the touchpad.

---

