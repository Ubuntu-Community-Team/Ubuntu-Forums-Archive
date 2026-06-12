---
title: "[SOLVED] Kensington Expert Mouse reassign button with xinput"
date: 2009-01-09
forum: Hardware
---

### Post by scrollheaven on 2009-01-09
My new Kensington Expert Mouse has the lower-right button (button 3 according to xev) assigned to right-click and the top-right button does nothing.

I'd like to use xinput to assign right-click to the upper-right button (button 8 according to xev).

There seems to be no setting for right-click in "xinput list-props 'Kensington Expert Mouse'"

I'm using Ubuntu 8.10 64-bit.

Could someone clue me in on how to do this? Clues for the clueless?:confused:

#### Forget it! ####

I used "xinput set-button-map  "Kensington      Kensington Expert Mouse" 1 2 8 4 5 6 7 3" which did the trick.

The below link tells how to make it permanent:

[http://ubuntuforums.org/showthread.php?p=6263089](http://ubuntuforums.org/showthread.php?p=6263089)

---

### Post by emergent on 2009-04-18
Late reply, but thanks. I have an expert mouse myself.

---

