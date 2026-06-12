---
title: "Split Ctrl keys"
date: 2008-10-24
forum: General Help
---

### Post by Terry Roman on 2008-10-24
Is there a way that I could remap the keys on the keyboard so that modifier keys (control, alt, shift, etc.) will only work as modifiers against the opposite hand, so a left handed shift will only affect letters on my right hand and visa versa?

I ask because I want to train my self to always use the opposite hand for modifiers and help prevent future rsi (yes, I'm an avid emacs user).  Or, perhaps, is there an easier way for me to train myself to always use opposite hands for modifier keys?

---

### Post by crom.osec on 2008-10-24
I don't understand what you really want: 
"left handed shift will only affect letters on my right hand and visa versa"
Can you provide an example?

---

### Post by unutbu on 2008-10-24
Welcome to the forums, Terry.
What you are asking to do sounds pretty cool, and I think it is possible, though I've never done this myself.

I think what you would need to do is make a custom keyboard layout.

For example, /usr/share/X11/xkb/symbols/us is the us keyboard layout.
Your /etc/X11/xorg.conf defines which keyboard layout you are currently using. (Search for the string 'XkbLayout').

The columns in the layout file (e.g. /usr/share/X11/xkb/symbols/us) define what a key does when a modifier like left shift or right shift is pressed. Typically, both the left and right shifts are globbed together, using a command like this in the layout file:
```

modifier_map Shift  { Shift_L, Shift_R };
```
Presumable, by creating a custom layout that omits this line, you should be able to treat them separately. (See [http://www.charvolant.org/~doug/xkb/html/node5.html](http://www.charvolant.org/~doug/xkb/html/node5.html), search for 'Shift_R'.)

In theory you should have complete control over what each key+modifier combo does.

To learn how to make a custom layout, you might find this guide useful:
[http://www.charvolant.org/~doug/xkb/html/node1.html](http://www.charvolant.org/~doug/xkb/html/node1.html)

At the end the author explains how he customized his own layout.

Good luck, and let us know how it goes!

---

### Post by Terry Roman on 2008-10-27
Thanks unutbu, I'll give it a try shortly.

In response to > **crom.osec said:**
> I don't understand what you really want: 
"left handed shift will only affect letters on my right hand and visa versa"
Can you provide an example?

Here are some examples: If I press right shift, I want it to shift for "asdfg" but not for "hjkl;".  If I press Control+x I want it to force me to use right control.

---

### Post by Terry Roman on 2008-11-03
Well, I've looked into it a bit and I just don't have the time to spend to do it.  If anyone else is able to get it working I'd love to hear about it.

---

