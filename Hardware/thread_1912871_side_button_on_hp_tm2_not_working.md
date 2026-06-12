---
title: "side button on hp tm2 not working"
date: 2012-01-21
forum: Hardware
---

### Post by thed0ctor on 2012-01-21
Hello,

I'm running Ubuntu 11.10 x64 on a HP Touchsmart tm2 and noticed that the side button that rotates the screen doesn't work.

I did some research and found several people had the same problem, eg [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/579534"). What i'm trying to do is find out the key event ID, this way I can map the button to a script that rotates the screen.

The only information I have on the button is that it's under xinput. It's named hp wmi hotkeys. I've done a xinput test 14 (where 14 is the id of the button), pressed it, and the console returns "key press 161"  "key release 161" 

The button doesn't appear to be a "keyboard" button, so I figured it's something like a "power button" or at least has the same "mapping properties" as the power button so I searched how the power button works. I found things on the powerbutton but the only thing I found enlightening is the event code or key that is mapped to a script that tells the computer to do whatever.

Being a CS major I'm thinking the event code is like the address to whatever is being pressed? I'm new to linux but want to help those who have a similar computer and have this issue.

Anyone who has fixed this problem on an HP or have any ideas on the matter that could reply would be great.

If you need more info let me know

Thanks

---

