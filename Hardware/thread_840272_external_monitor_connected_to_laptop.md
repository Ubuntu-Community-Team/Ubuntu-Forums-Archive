---
title: "external monitor connected to laptop"
date: 2008-06-25
forum: Hardware
---

### Post by siva_ on 2008-06-25
Hi,

I have a dell xps m1210 laptop. I just installed Ubuntu, and almost everything works perfect.

When I used to have windows installed, here's how it would work with an external monitor:

1. Plug it in to the laptop and hit Fn+crt/lcd
  a. That function key would toggle between the monitor and the lcd (or both).

2. When I unplug the monitor it would revert back to the LCD (Or I would have to hit the Fn+ctr/lcd button)

On Ubuntu, using the Nvidia config tool, I set it up to work in Twin view. But the problem is, when I disconnect the monitor, I'm not sure how to tell it to go back to the lcd because the Fn+ctr/lcd button doesn't work on my ubuntu install.

Because the Panels are set to my external monitor, after I unplug the monitor (to take the laptop somewhere else), I'm left with a blank screen on my laptop (fully functional, with right click menu, but no upper/lower panels).

I also tried using the Nvidia tool to set it up in Dedicated mode, so each screen has it's own desktop. I liked this better, but I couldn't figure out how to move windows between the two different screens. 

Thanks for the help.

---

### Post by phidia on 2008-06-25
There is a related thread [here]("http://ubuntuforums.org/showthread.php?t=764033&highlight=twin+view") perhaps the OP's solution provides some help on that?
The community docs, unfortunately are very limited on help with twinview.

---

### Post by Tharmas on 2008-06-25
Did you try System > Preferences > Screen Resolution ? (this in the ubuntu menu, don't know about xubuntu)
You have there all you need, I guess.
Or else, open a terminal and type "man xrandr"
xrandr is a powerful tool. 
It solved all my problems in lectures struggling with ubuntu, projectors, and malicious grins from windows users in the audience.

---

