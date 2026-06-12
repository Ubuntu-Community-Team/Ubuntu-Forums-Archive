---
title: "Laptop numlock key turns itself back on!"
date: 2009-05-12
forum: Hardware
---

### Post by v0idnull on 2009-05-12
System: ASUS M70v series

This is a 17in laptop so due to its size it has a numpad. Unfortunately, the numlock key keeps getting turned off on its own for reasons I do not understand! I could turn it off, hit 7/Home, cursor goes to beginning of line, realize that's not where I wanted to go and so I hit 1/End and the number 1 keeps being written.

Does anyone have any idea why this is happening and how I can fix it?

---

### Post by Macchi on 2009-05-12
I can think of two possibilities:

1) Any BIOS settings that could affect it? Less probable because it normallyaffects only the on of off state upon system start.

2) On Ubuntu goto System->Preferences->Keyboard, Layouts Tab, Layout Options Button and check the settings around Numeric Keypad.

Hope you will find any settings that may cause the behaviour you describe. There is also a possibility that the keyboard layout settings may cause the problem.

---

### Post by v0idnull on 2010-01-29
I didn't resolve my issue when I first posted this. Today I did a search on google for the same problem and found this post in the first result.

Realizing I'm screwed, I followed your advice and played around with layout options.

I resolved this issue by doing:

Preferences -> keyboard -> layouts -> layout options -> Miscellaneous Compatibility Options -> and checked Default Numeric Keypad Keys

Hopefully this will help other people with similar problems

---

