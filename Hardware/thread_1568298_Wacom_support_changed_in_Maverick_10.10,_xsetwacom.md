---
title: "Wacom support changed in Maverick 10.10, xsetwacom no longer supports &quot;core keys&quot;"
date: 2010-09-05
forum: Hardware
---

### Post by e.m.fields on 2010-09-05
Hiya. 

I'm enjoying Maverick 10.10 Alpha 3 very thoroughly, and looking forward to the (eventual) inclusion of a perfected working wacom driver. 

**Unfortunately, the newer version of xset-wacom included in the default wacom drivers repository doesn't seem to support non-alphanumeric keys I was using without problems in 10.04.**

Upon trying to configure, for example, 
```
xsetwacom set "Wacom Bamboo pad" Button4 "core key control z"
```
I'm getting error message:
```
Note: The "core" keyword is not supported anymore and will be ignored.
```

So, wacom man page says there's a list of "modifier keys" which can be accepted, including Control/Alt/Super/F1-F40.
(F40?)

(You can view the list by typing:)
```
xsetwacom list mod
```

But unfortunately, I can't do something as simple as set a non-alphanumeric key... for example, the "plus" symbol "+", or anything of the like.

Could anyone please tell me this is not so, and how to change or set a non-alphanumeric key to a function?

---

