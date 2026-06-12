---
title: "Fglrx problem with HL-based applications in Wine"
date: 2012-02-08
forum: Hardware
---

### Post by 8bitpalace on 2012-02-08
Hey,

I'm running Ubuntu 11.10 with a AMD Radeon HD 6xxxM series graphiccard. Recently I've had some serious problems with running Half Life-based applications in Wine which all used to work fine. Those include Counter-Strike 1.6 and Day of Defeat for now. I'm using Steam to play those games. 

After a while in a multiplayer game the whole xorg crashes, I can't do anything and have to hard-reset my computer. And due to that, I'm sorry to say that I've been unable to grab a terminal output of the problem. 

I've tried different Catalyst drivers including 12.1, 11.12 and 11.10. I know that I've had no problems with 11.12 and 11.10 before, but now all of a sudden this happens. Also tried different wine versions, 1.4-rc2, 1.3.37 and 1.3.19 (which I used to run the applications with before). It is also not a "gameoverlayrenderer.dll" (which is a known crash-problem when running games with Steam using Wine) I've changed it off and on helplessly as well as changing compatible Windows versions in winecfg.  

After some serious searching at the web my conclusion is that this might have to do something with running opengl-applications in wine using fglrx. All though, switcihing from opengl to D3D in video settings still hangs xorg. Strange thing is that all used to work fine once..  

I have yet to find a solution to the problem, any help is appreciated. 

Regards,
8bitpalace

---

### Post by 8bitpalace on 2012-02-09
bump

---

### Post by 8bitpalace on 2012-02-10
Have now purged both fglrx and xorg and then reinstalled them a couple of times, still no luck. Would love if anyone had a clue, don't want to reinstall Ubuntu from scratch if it is in vain.

---

### Post by 8bitpalace on 2012-02-14
Currently solved by dual-booting Win 7.. sucks.

---

