---
title: "G200, BNC and SyncOnGreen"
date: 2005-07-29
forum: Hardware &amp; Laptops
---

### Post by pablored on 2005-07-29
Hello all,

I'm currently wrestling with a small desktop that isn't playing ball.  Basically I want the Matrox G200 graphics card to output to my monitor (LG 915FT Plus) through a BNC connection (R G B - 3 wire) so I can share the screen between two pcs without changing cables or buying a switch.  The monitor has both DSUB and BNC inputs.  I have had this working before with an old PA-RISC debian machine, unfortunately that is nolonger available to look at.  In that case it just worked.  

At the moment I have the sync on green bit working through the DSUB, in the xorg.conf I have added Option "SyncOnGreen", but I just can't get it going through the other cable.  I get an image of sorts but squashed and blank colour (if that makes any sense).  Anyway, I'm hoping the cable hasn't perished :/ 

Has anybody any experience with this kind of set up?  My only thought at the moment, is I could need some explicit timings in the xorg.conf or something... but I'm a little tired and it is late.  

Thanks
Paul

---

### Post by pablored on 2005-07-31
I have given up on that idea, unsolved, and have chosen a different strategy: xvnc.

---

