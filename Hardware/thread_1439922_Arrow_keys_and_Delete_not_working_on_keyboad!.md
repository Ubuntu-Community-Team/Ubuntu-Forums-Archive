---
title: "Arrow keys and Delete not working on keyboad!"
date: 2010-03-26
forum: Hardware
---

### Post by mayank.abhishek on 2010-03-26
I an running Karmic. Recently my keyboard has started behaving oddly.
It does not respond to three arrow keys and the delete key. I also have Win7 installed on another partition. The keys work fine there.

I did,
```
xev | grep -A2 --line-buffered '^KeyRelease' | sed -n '/keycode /s/^.*keycode \([0-9]*\).* (.*, \(.*\)).*$/\1 \2/p'
```

And got the following results:
Key Pressed: Output on Screen
Left arrow: 113 Left
Right arrow: 156 XF86Launch1
Up arrow: Nothing is displayed
Down arrow: 200 NoSymbol
Delete: 200 NoSymbol

Onscreen keyboard, onBoard works fine!

Please help!

---

