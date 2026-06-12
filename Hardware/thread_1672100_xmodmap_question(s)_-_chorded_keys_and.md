---
title: "xmodmap question(s) - chorded keys and"
date: 2011-01-20
forum: Hardware
---

### Post by Jmob on 2011-01-20
Brand spanking new Ubuntu/Linux user here.  I'm just starting out, but I'm already wanting to modify a few things to get my user experience back to what I like, so I've got to climb this learning curve.

I've been trying to remap a few keys with Xmodmap.  Specifically, I'm trying to kill the Forward and Back buttons that are placed dangerously close to the arrow keys on my Thinkpad.  I think I could handle that, based on what I read--I could just remap it to PgUp and PgDown like I did with Keytweak back on Win7.  That allowed me to hold Ctrl and have a quick tab-switcher in Firefox, which I liked.  

But since I'm learning, I realize I don't quite understand what I'm getting with "xmodmap -pke", and the explanations I've seen so far don't include the whole thing.  

Pulled a few examples from the readout at random.  Using the example for 28 below, you have four t's following the keycode.  I understand  two symbols t and T is with or without Shift modification, but what are the remaining two?  And while I get the significance of  "NoSymbol" in the example of 37, whats the general form that reconciles these two formats?

```
keycode  28 = t T t T
keycode  29 = y Y y Y

or

keycode  37 = Control_L NoSymbol Control_L

```

The idea that brings me to this is that I'd like to consider mapping Forward and Back to Ctrl+PgUp and Ctrl+PgDown, which would mean they're dedicated tab-switching keys.  More useful to me than the default, anyway.  So if the answer to how to do this is not contained in the above, how would I go about this?

Thanks in advance.

---

