---
title: "WACOM intuous 2 freezes X"
date: 2015-11-27
forum: Hardware
---

### Post by federico-prato-t on 2015-11-27
Hello, 

recently i started suffering of carpal tunnel, so got an intuous 2. Installing the wacom linux drivers it worked quite nicely for a while, then it stopped working after i updated my system to the last kernel. 

I installed the latest versions of the drivers and so on, but no luck. Everytime i plug the tablet in X freezes and there's no way of getting it back again :(. Before it freezes though i can still type 

```
xsetwacom list
```

and the device is there.

in the X logs i found

```
These backtraces from mieqEnqueue may point to a culprit higher up the stack.(EE) [mi] mieq is *NOT* the cause.  It is a victim.
(EE) [mi] EQ overflow continuing.  100 events have been dropped.
```

that could be related?

thanks a lot for helping me out :)

---

### Post by federico-prato-t on 2015-11-27
Well, using the past kernel everything works, so i guess it is fixed?

thanks

---

