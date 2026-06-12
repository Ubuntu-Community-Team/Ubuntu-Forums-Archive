---
title: "Vaio Composite Video TV Out"
date: 2005-03-28
forum: Hardware &amp; Laptops
---

### Post by mathmatt on 2005-03-28
I am unable to get my Vaio to display on a TV using a composit video out (to RCA).  I tried atitvout which recognizes the TV when it is pluged in.  I can even see a flicker on the TV (which is set for video input) when i try to send the signal to the TV.

Has anyone experienced this issue or know how to get video out from my Vaio FXA47?

-Matt

---

### Post by luiska on 2005-04-12
Hi

Will some eXperienced people please help with this, I have the same thing happening. The beauty of the whole thing is that when the TV is plugged in, I can see the bootup process and when I tried it with a the "liveCD" I can see the splashscreen. 

The problem seems to be when X starts. Then the TV just flicker, some settings is not correct or missing. What settings, now that is the question! 

The machine is a Compaq Armada E500 and the videocard is ATI Rage Mobility A/P 2xAGP. 

I have installed the atitvout package and it detect everything just fine. The composite out isnt dead, there is something on the TV screen!

It would be creatly appriciated if someone can help with some of the options that I can try.

Thanks in advance
Luiska

---

### Post by xx404 on 2005-10-20
I've read that the atitvout utility doesn't work with the Xorg server but it does with the XFree86 server. That's probably why you see the output on your TV until the X server starts. You could also try experimenting with your mode lines in the xorg.conf file to see if it's a modeline problem.

I'm going to look into GATOS to see if there is an alternative solution to atitvout.

If someone could tell me how to determine which driver Xorg is using that would be a good start.

---

### Post by mathmatt on 2005-10-20
xx404,

Thanks! Let me know what you find about GATOS.  Also, I just upgraded to Breezy, and haven't tried to replicate the problem.  I suppose I should see if the issue still exists under 5.10.

-Matt

---

