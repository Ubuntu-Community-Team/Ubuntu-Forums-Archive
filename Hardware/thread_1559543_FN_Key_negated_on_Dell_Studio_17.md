---
title: "FN Key negated on Dell Studio 17"
date: 2010-08-23
forum: Hardware
---

### Post by lorgonjortle on 2010-08-23
Hey there,
     I've recently (within the past month) purchased a Dell Studio 17 Laptop, and I'm using Ubuntu 10.04 x64. The function keys (F1, F2, F3, et cetera), when pressed alone, perform their "special" tasks, such as changing the brightness or volume. The odd thing is the buttons should only perform these tasks if the FN is pressed. So I tried pressing the FN key down and pressing some function keys. When it is down, the FN keys perform their normal tasks, such as F5 in Firefox to refresh, or F6 in Netbeans to run the current project.

So my question is: Is there anyway to negate my (already negated) FN button so that Ubuntu doesn't always treat it as if its down?

EDIT: New info
I've tried running 
```
xev
```
to catch X events to see if X is handling the FN key. When I press FN, X doesn't capture an event. Moreover, if I press F6 (toggles the keyboard backlight), it throws no event. BUT, if I press both FN and F6 (to get the "normal" F6 function), X captures the event and handles it. So this is just more proof that my FN is negated... but I'm not sure it helps at all. :P

Thanks for any help!

---

### Post by mipper on 2010-09-20
I too have a Dell Studio 17 and have the same issue - though I believe it's by design rather than an error in Ubuntu.  The same behaviour is evident in Windows and the colouring of the labels on the function keys indicates that you're expected to combine them with the Fn key to get the normal FX behaviour.

God only know who in Dell thought this was a good idea.  It's driving me nuts.  Does anybody have any ideas as to how to reverse this setting?

Cheers.

---

### Post by mipper on 2010-09-20
Ah, just discovered a setting in the BIOS to change the FN key behaviour

[LIST]
[*]Press F2 on boot
[*]Advanced -> Function Key Behaviour -> Function Key First
[/LIST]

---

