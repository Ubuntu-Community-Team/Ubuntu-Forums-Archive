---
title: "Remap Mouse Buttons"
date: 2014-04-30
forum: Hardware
---

### Post by schowell on 2014-04-30
I recently upgraded to Ubuntu 14.04, Tahr, (complete reinstall) and now my mouse buttons are jumbled from what they were in 12.04, Pangolin.  
I am using the Evoluent VerticalMouse 3 (Rev 2), probably not a very common mouse but I like it ([http://www.evoluent.com/vm3.html](http://www.evoluent.com/vm3.html)). 
Specifically:

[LIST]
[*]Button 2 used to be right click but is now middle click (the same as when I press on the scoll wheel, button 4) 
[*]Button 3 used to be back navigation is now right click 
[*]Button 5 used to be forward navigation is now back navigation 
[/LIST]
This leaves me with no forward navigation. More importantly, I keep pressing a button to get unexpected results.  I know I can relearn to use my mouse but is there a good method for changing this behavior?

---

### Post by Katzinski on 2014-04-30
Xserver could be used to solve that. I've not yet tried that myself. My starting point would be [evdev]("http://manpages.ubuntu.com/manpages/trusty/man4/evdev.4.html") and [xorg.conf]("http://manpages.ubuntu.com/manpages/trusty/man5/xorg.conf.5.html"). Sorry for giving just a bit of an answer.

---

