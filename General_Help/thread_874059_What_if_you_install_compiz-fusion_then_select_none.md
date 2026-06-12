---
title: "What if you install compiz-fusion then select none ?"
date: 2008-07-29
forum: General Help
---

### Post by AgentZ86 on 2008-07-29
HI

What if you install compiz-fusion then create the cube etc. and all working well.

But then I wanted to sort of turn it off to play eve and see the effects it would have on game play ?

So I went to System/Preferences/Appearance

And selected none for no effects etc. 

Now I can't figure out how to turn compiz-fusion again

Please advise thanks ?

---

### Post by ladr0n on 2008-07-29
Check either the "maximum" or "custom" options in the Appearance dialog and use compiz config settings manager to set compiz back up (I assume you have it installed if you had the desktop cube).  For future reference, use the commands "metacity --replace" to temporarily switch compiz off for gaming and "compiz --replace" (or logout and log back in) to switch it back on.

---

### Post by chavanak on 2008-07-29
open a terminal and type in "compiz --replace" (without quotes). 
The better option is to install fusion-icon from the repo and add it as a startup program (System --> Preferences --> Sessions). 

To install it open a terminal and type in "sudo apt-get install fusion-icon.
To run it at startup go to sessions, press add and type fusion in the first box and in the second type "fusion-icon" (without quotes).
Then when you don't want any effects right click on the fusion-icon in the system tray and select metacity for compoistion.
Cheers

---

### Post by AgentZ86 on 2008-07-29
Linux is soooo cool

Both solutions work well, I decided to install the Fusion manager button etc.

Thanks all.

Please see this thread to find out why I needed that, perhaps you can help with my EVE online install ?

It's related to this subject I'm sure ?

[http://ubuntuforums.org/showthread.php?t=605368](http://ubuntuforums.org/showthread.php?t=605368)

However the Ubuntified client I never could get working, but I'm close to playing with just the EVE windows install with wine ?

Not sure why, but it does work partially and not always, but I did get it working ?

Please see that thread and see if you have any ideas please
Thanks

Thanks again for the help with turning on/off fusion

---

