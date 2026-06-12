---
title: "Intrepid on Samsung Q45"
date: 2008-11-12
forum: Hardware
---

### Post by radiobuzzer on 2008-11-12
Hi, I have just finished an upgrade from 8.04 Hardy to 8.10 Intrepid, on my 4-months-old Samsung Q45 (model NP-Q45A00A in particular). 

I would like to present my impressions and discuss with other users of this -not so popular- laptop about the problems and the improvements.

Positive steps:
[LIST]
[*]Intrepid is the first release that brightness adjustment actually works! Much more energy saving now. Though, there are still some issues. See below. 
[*]The battery indicator is much more realistic. Previously I would get a 2:30hrs remaining time estimation, but I am sure it lasted for 4hrs. Now I get the 4hrs promise from the beginning

[/LIST]

Issues that are still there:
[LIST]
[*] Wireless adapter still can't be disabled by keyboard. I can indeed disable all the wireless connections from the network manager tool on the appbar, but I don't think this saves as much energy a good switch-off would save.
[*] Some special buttons are still not mapped. Like the Fn+F5 , Fn+F2 (I think this worked before), Fn+F3 etc. and the Mail button. There should be a workaround for these.
[/LIST]

Things that go wrong:
[LIST]
[*] The brightness adjustment keystroke, when used, causes the X server to freak out. In particular you hold Fn and then you press the UP arrow just once. This should cause the brightness to increase just one step. Instead, it keep increasing until it reaches the top. You can stop this furious increase middle way by pressing another key really fast.
But THEN! the X environment sort of freaks out:
[**]You can use the left and right click on all windows, but you can't move the windows. You can't type anything in the windows. 
[**]you can't use the Menus on the menu bar.
[**] if you've actually reduced the brightness, it will go till zero and you want be able to increase backlight again.
This is FIXED if:
[**]You violently restart the X-server (Alt+Ctrl+Backspace) or
[**]you use the keys for increasing the backlight (Even if it doesn't work and you don't see anything). Then you switch to a terminal screen (Alt+Ctrl+F2) and the back to the X server [Alt+Ctrl+F7]. Interesting, huh?
[*]Since, as said before, when brightness gets to zero, you have no chance of increasing it again, same is the problem when this happens automatically. So, if you had set "Energy Settings > On battery Power > Dim display when idle ", the display would arbitrarily dim to zero and then wouldn't go back when you resume your work. The solution is of course to disable this option
[*] It just happenned that my brightness keeps slowly dicreasing, without reason. Then it get's to zero and have the same problems as before. I can reset it as explained, but I can't understand why is this, since I have disabled the previous option.
[/LIST]


Namely, if other people have the same problems, I would summarize that the source of them are 
(a) the bad effect of the brightness keystroke on the X system
(b) the fact that if brightness goes to zero, it can't be increased again.

possibly. Give me your feedback!

---

### Post by baudot on 2009-03-22
I'm facing the same problems here on my Samsung Q45.

---

