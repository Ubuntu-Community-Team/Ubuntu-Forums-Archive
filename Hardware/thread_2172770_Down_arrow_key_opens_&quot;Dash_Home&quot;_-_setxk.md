---
title: "Down arrow key opens &quot;Dash Home&quot; - setxkbmap issues"
date: 2013-09-06
forum: Hardware
---

### Post by kenip on 2013-09-06
I have 2 keyboards, a Microsoft Wireless 800 and a Logitech Wireless K350.  With both keyboards pressing either the **Down Arrow **key or **End** key opens the Dash Home. 

[LIST]
[*] I checked my Keyboard Shortcuts and that isn't the culprit 
[*]I tested what key press is actually detected using the Keyboard Shortcut utility and **Down Arrow**  results in a "Mod2 + Super R" and the **End** key gives a "Super L". 
[/LIST]
  Playing around with setxkbmap gives the following:
```
setxkbmap -query

rules:      evdev
model:      microsoftmult
layout:     us
``` 
Now the layout is already **'us'** but if I execute the following:
```
setxkbmap -layout us
``` 
**Down Arrow** now works except that holding it down does not result in scrolling down in any window.
If I restart the system I get the same flawed behavior of the down arrow.  In addition, if I swap out the keyboard to the Logitech and change the model by:
```
setxkbmap -model logii350
```
This seems to correct the behavior of the down arrow but still I cannot use it to scroll down.

I've been trying to fix this issue for literally months and I just can't figure out what is going on.

---

