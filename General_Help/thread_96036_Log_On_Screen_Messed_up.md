---
title: "Log On Screen Messed up"
date: 2005-11-28
forum: General Help
---

### Post by DaGGer on 2005-11-28
ok well i install ubuntu and everything went fine and then when i try to start it up and log on for the first time the log on screen is all scrambeled.  I don't know how else to explain it.

---

### Post by aysiu on 2005-11-28
What happens when you press Control-Alt-F1?

---

### Post by daveyl on 2005-11-28
Do you mean scrambled as in fuzzy?

If so, then it might be a default display resolution problem.
To see if thats it, log onto the fuzzy ubuntu, then find go to SYSTEM>PREFERENCES>SCREEN RESOLUTION...play around with different ones until  the screen doesnt look like crap. If you find a good one, then next step is setting that up as your default resolution (which I did once, but forget how just now) - - if thats the problem post back and Ill figure it out again and post it.. if not I wont have to).

Ps - I may we WAAY off on this, but i remember having a similar problem before fixing my resolution.

---

### Post by DaGGer on 2005-11-29
ok well i tried that ctrl-alt-f1 and it didn't do anything it stayed the same, do you think that maybe i need a new hard drive or do i need to completely redo my harddrive because right now i have a 50-50 split with windows xp

---

### Post by mccrank on 2005-11-29
I have a similar problem the login looks not to bad disregarding the fact that the mouse cursor is missing but after i login the display becomes awful and if i try to open anything it freezes.

---

### Post by guardianangelz on 2005-11-30
i agree with daveyl, it's most likely a display resolution problem.  my laptop has a 1400x1200 screen (funfun!) but that always means every time i install Linux i have to expertly navigate the fuzzy messed-up screen to get to the control settings thing.  i have some linux genius friends around me, so i'll ask around for the terminal commands to change the default resolution.

---

### Post by teaker1s on 2005-11-30
sudo dpkg-reconfigure xserver-xorg you may need to hit escape at boot and select recovery to be able to see well enough to configure it

---

### Post by Edit on 2005-11-30
It could be a graphics driver problem.

Hitting Ctrl + Alt + F1 really should get you to a Console though, regardless of either resolution or driver issues.  Try Ctrl + Alt + F2, F3, F4, F5 and F6 too and see if any of them magically appear.

What kind of graphics card do you have?  Or if it's onboard graphics, what kind of motherboard do you have?

-Edit

---

### Post by DaGGer on 2005-12-01
currently i have a Radeon 9200(i got it for free) and its not my screeen resolution because i can't do anything i can't login or anything.

---

