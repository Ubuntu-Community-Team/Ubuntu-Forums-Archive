---
title: "howto get mathematica keys working on laptop"
date: 2007-02-05
forum: Hardware &amp; Laptops
---

### Post by mikesf on 2007-02-05
If you have mathematica running and the keys are not working correctly, e.g. the escape key doesn't work, or shift-enter or any of the formating like super-script and sub-script, then this is an issue with your num-lock key. TURN IT OFF. if you have a laptop like i do (toshiba u205) then the numlock key is fn-f11 and turning this on and off doesn't make a difference.
So wolfram has a fix for this which is posted at their site:
[http://support.wolfram.com/mathematica/systems/linux/general/configurenumlock.html](http://support.wolfram.com/mathematica/systems/linux/general/configurenumlock.html)
basically, you just create a line in .Xresources (create that file if it doesn't exist) in your home dir
*secondaryModifierMask: Mod3Mask
and then save, then restart x or even easier just reload the x settings with
$ xrdb -load ~/.Xresources
and then everything should work when you restart mathematica!

---

