---
title: "Double-click button"
date: 2005-12-08
forum: Hardware &amp; Laptops
---

### Post by Thunk on 2005-12-08
How do I assign "double-click" to my thumb button?

I tried using imwheel but I can't find there how to assign double-click to a button.

---

### Post by chenel on 2006-06-06
[QUOTE=Thunk]How do I assign "double-click" to my thumb button?

I tried using imwheel but I can't find there how to assign double-click to a button.[/QUOTE]

I know this thread is ancient by now, but if you still care --

In your .imwheelrc file in your home directory (using the /etc/X11/imwheel/imwheelrc file never seemed to do anything for me), you can put this at the end:

```

".*"                      # applies to any application
None, Left, Button1, 2     # no modifiers, button to look for is 'Left', assign two clicks of Button 1 to it

```

assuming that your thumb button is mapped to "Left" by Imwheel like mine is.  If not, adjust accordingly.

Hope that this helps!

-Jeremy

---

