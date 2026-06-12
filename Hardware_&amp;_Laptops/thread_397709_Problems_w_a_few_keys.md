---
title: "Problems w/ a few keys"
date: 2007-03-31
forum: Hardware &amp; Laptops
---

### Post by Europa2010AD on 2007-03-31
I have a MS Natural Keyboard (the most plain and simple model -- w/o any special function keys). For some reason, when I try to type the double quote (") or the tilde (~), I always have to press the keys twice before they'll show up on screen. And the double quote that shows up on screen doesn't look right neither (it's a double quote alright, but just doesn't look normal... it appears as if it's a special character).

I have my keyboard profile set to "MS Natural Keyboard" and the input layout to "U.S. International". I have tried the rest of the U.S. input layouts and the problem persists. Does any one have any idea how I can solve this issue?

---

### Post by Europa2010AD on 2007-03-31
Does anyone have any idea? I´m running Edgy, if that helps....

---

### Post by phutkins on 2007-06-04
I had a very, very similar problem, and I think I found a partial answer... 
For me, it was that the Ubuntu Feisty Fawn installation detected an international keyboard for my Sony Vaio laptop.    I went to System -> Preferences -> Keyboard, chose the Layouts tab, asked it NOT to use the X configuration, added a non-international keyboard layout variant and deleted the international one.  I found the directions and help here:  
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_keyboard_layouts_for_other_languages](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_keyboard_layouts_for_other_languages)
[http://ubuntuforums.org/showthread.php?t=222605](http://ubuntuforums.org/showthread.php?t=222605)

This seems to be the most direct method of fixing this problem.  However, I'm not convinced that it's the proper way to fix it.  For instance, I still have this problem in the regular non-X terminals (what you get at Ctrl-Alt-F1).  I think the real problem is that the keyboard type was chosen incorrectly at installation time.  I'm not sure what other configuration settings have dependencies on the value ("screen" for instance?)... but I'm sure I'll need to go change them as well.   Is there a way to change it for the whole OS without having to reinstall or go back in time?

See also: 
[http://ubuntuforums.org/showthread.php?t=50501](http://ubuntuforums.org/showthread.php?t=50501)

(Note: I installed the Xubuntu variation, but this should be applicable for straight Ubuntu as well)

---

