---
title: "Display 'issues' during live boot"
date: 2007-06-11
forum: Hardware &amp; Laptops
---

### Post by twistie on 2007-06-11
I just built a 'new' linux box because I finally got a graphics card for it. Note: IU have 3 others so there is no big hurry to get this onje running. So I have a copy of Edgy lying around, load it in, boot up on the CD... But as soon as X starts I get a while pile of different colored vertical lines which repeat across the screen. So I press Ctrl+Alt+Backspace to exit X and the screen flickers but X automatically restarts. One not to be stumped by this I hit  Ctrl+Alt+F2 and the screen changes but instead of me actually being able to read it I just get a whole pile of black and white vertical lines in the same repetitive pattern as before.

So I think to myself. Maybe its just Edgy, so I load in Dapper only to find that it to has exactly the same problem. EXCEPT on Dapper I can get into bash. I was inclined to think it was just the X server doing one of its crazy bad driver things but when it did it in the bash prompt on edgy it really got me stumped. I'm downloading Feisty as we speak. But I doubt it will work aswell. Can anyone tell me what the hell is going on?

Here are the stats for the comp

Pentium 3
256 MB RAM
Inno3d Geforce 6600 Gt
and thats about it...

EDIT: Just tried to reconfigure the X server on Dapper with no success


DON'T WORRY I JUST TRIED THE OTHER PORT ON THE CARD AND IT WORKED. 
I also forgot to mention that I have tried booting in Safe Graphics mode.

---

### Post by brim4brim on 2007-06-11
We had a problem like that and it turned out to be a screen resolution detection problem.  It was in the wrong resolution and we started getting weird lines across the screen.

Doesn't happen across the entire screen though as we were able  to just change the resolution using Gnome so I don't know if it'll help you out.  Just throwing it out there.

---

