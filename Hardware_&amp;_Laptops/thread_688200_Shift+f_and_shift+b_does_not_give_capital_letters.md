---
title: "Shift+f and shift+b does not give capital letters"
date: 2008-02-05
forum: Hardware &amp; Laptops
---

### Post by CalvinMcGee on 2008-02-05
I'm using gutsy gibbon on my thinkpad laptop.

Two issues:
Firstly I am using swedish version. And I can't get the key combinations: shift+f and shift+b to produce capital letters. Just nothing happens, sometimes it just jumps out of the field I'm working with. This problem is in all ubuntu, firefox, OpenOffice and so on. It works fine to produce capital F and B with the Caps-lock.

Secondly, often when i'm at home I have the NumLock key on. However when I don't have my external keyboard, I can't turn off the NumLock. The worst thing of all is that when I shut down and reboot, the numlock is still on when I login. On thinkpads the key combination for numlock should be shift+Scrolllock/Numlock button. I have looked some at thinkwiki.org, and apparently I'm suppose to use xmodmap, but I don't understand the instructions given there, because the file I'm suppose to edit doesn't exist.

Please help!

---

### Post by CalvinMcGee on 2008-03-16
Couldn't someone please help me. This have bothered me for several months.

> **CalvinMcGee said:**
> I'm using gutsy gibbon on my thinkpad laptop.stort b

Two issues:
Firstly I am using swedish version. And I can't get the key combinations: shift+f and shift+b to produce capital letters. Just nothing happens, sometimes it just jumps out of the field I'm working with. This problem is in all ubuntu, firefox, OpenOffice and so on. It works fine to produce capital F and B with the Caps-lock.

Secondly, often when i'm at home I have the NumLock key on. However when I don't have my external keyboard, I can't turn off the NumLock. The worst thing of all is that when I shut down and reboot, the numlock is still on when I login. On thinkpads the key combination for numlock should be shift+Scrolllock/Numlock button. I have looked some at thinkwiki.org, and apparently I'm suppose to use xmodmap, but I don't understand the instructions given there, because the file I'm suppose to edit doesn't exist.

Please help!

---

### Post by Ace2016 on 2008-03-16
Is everything working fine in windows? i ask just for comparison because i had some hardware issues with my pavilion which seemed like software issues at first but later turned out to be worse

---

### Post by CalvinMcGee on 2008-03-16
Yes, it works fine in Windows. I managed to get the numlock key to work by typing
>  xmodmap -e 'keycode 77 = Num_Lock'
However this is really annoying me. Not getting shift+f, and shift+b to get capitalised letters
I'm thinking maybe I could change something in xmodmap to get it to work, but I don't know what keycode to use.

---

### Post by Ace2016 on 2008-03-16
Have you considered creating yourself a custom keyboard mapping? this will probably fix you're issue:

[http://people.uleth.ca/~daniel.odonnell/Blog/custom-keyboard-in-linuxx11](http://people.uleth.ca/~daniel.odonnell/Blog/custom-keyboard-in-linuxx11)

I found this guide when trying to fix my problem which ended up being a bios issue, never had a chance to try it out so i don't know if it will work for certain but its a good starting point.

---

