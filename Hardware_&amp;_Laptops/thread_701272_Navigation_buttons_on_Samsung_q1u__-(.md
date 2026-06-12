---
title: "Navigation buttons on Samsung q1u  :-("
date: 2008-02-19
forum: Hardware &amp; Laptops
---

### Post by nieilnjie on 2008-02-19
&#65321;install ubuntu 7.10 desktop on my new Samsung q1 ultra umpc.
and looks great. however, the navigation buttons do not work.
I have tried xev, when I click the buttons, nothing appeared. Does this meaning ubuntu don't know these buttons exist?
It is said that there is a UME version of ubuntu, which is tested on q1 ultra, so I think somebody has solved this problem. How can I find the fix and merge to my desktop version?
Please help.
Thanks a lot.

---

### Post by weid83 on 2008-04-04
I'm running hardy heron beta and can get the navigation buttons/menu button/dial pad key to work by using setkeycodes to make it into a known key.  If you run dmesg after pressing one of the keys you should get something like:

atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.

where e078 will correspond to the key you just pressed.  Hope that helps.

---

### Post by weid83 on 2008-04-04
Here's a script that will set up the hardware keys

#!/bin/bash

# Down
setkeycodes e059 108
# Up
setkeycodes e058 103
# Left
setkeycodes e056 105
# Right
setkeycodes e057 106
# Dial Key - <F2>
setkeycodes e078 60
# Menu - <F3>
setkeycodes e054 61

---

