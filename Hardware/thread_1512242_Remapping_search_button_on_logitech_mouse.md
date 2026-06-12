---
title: "Remapping search button on logitech mouse"
date: 2010-06-17
forum: Hardware
---

### Post by capsskinsterps on 2010-06-17
I have a Logitech MX620 mouse. It has a search button on it that works exactly like its supposed to: when pressed it will open a search window. In Windows, I can use Setpoint (Logitech's driver software) to remap that button to a variety of different functions. I have it set to the middle mouse button. I am trying to accomplish the same thing in Ubuntu 10.04 but am having trouble because the button does not map to a mouse button. Using xev I get the following results:


KeymapNotify event, serial 36, synthetic NO, window 0x0,
    keys:  4294967207 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   2   0   0   0   


In Ubuntu's default keyboard shortcuts manager, if I press the search button to set it for any random event, it gives me the message:

"The shortcut 'XF86Search' is already used for 'Search'"

From this it would seem that the search button on my mouse maps to a keyboard key, specifically XF86Search.

So finally, the actual question. How can I map a keyboard shortcut, in this case "XF86Search" to a mouse button? Or, better yet, how can I have Ubuntu recognize the search button on my mouse as a mouse button? Help on either of these would be greatly appreciated.

---

