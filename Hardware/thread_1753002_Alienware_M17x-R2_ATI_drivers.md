---
title: "Alienware M17x-R2 ATI drivers ?"
date: 2011-05-08
forum: Hardware
---

### Post by Hakri on 2011-05-08
Hello everybody,

     I am sorry if somebody already asked that question, I did a research and all I have found is for Alienwares m17 with NVIDIA graphic cards.  Mine has ATI.

     So, here is a 'quick' info about my problem : When I bought my Alienware m17x-R2 (Post-Dell), I choose a crossfire with ATI Radeon Mobility 5870 graphic cards.
Here is the paradox that happened as soon as the computer was delivered :
-When I bought the computer, I explicitly choose two ATI Radeon Mobility 5870 set up in a crossfire (I know, I just said that).
-When I installed ATI's drivers for the ATI Radeon Mobility 5870, the computer became as powerful as a calculator (I had like 8 FPS when I tried to play the first Half-Life, you don't even want to know about Crisis, Portal, etc.)
-When I installed Dell's drivers for the ATI Radeon Mobility 5870, the computer became as powerful as it was supposed to be. (Great FPS with any game I tried, even the first Half-Life, Crysis, etc.)
-When I installed Dell's vBIOS update for the ATI Radeon Mobility 5870, I've got an error message saying "This vBIOS update is for ATI Mobility Radeon 5870 ONLY".  Meaning "You don't have an ATI Radeon Mobility 5870".

So now my problem is : On Ubuntu, whatever driver I use (The one Ubuntu tells me to use, the one from ATI, or none, since Dell didn't make any Linux driver for its hardware), my computer remains as powerful as a calculator.  I would like to know if anyone had any idea how I could have the right driver that could make my graphic card function normally (and using the crossfire if possible), please.

If you have any question, don't hesitate.

Thank you in advance.

---

### Post by nerdy_kid on 2011-05-08
you'll probably want to post the output of this:

```

lspci | grep VGA

```

---

### Post by Hakri on 2011-05-08
Here's what it says :

> 02:00.0 VGA compatible controller: ATI Technologies Inc Broadway XT [Mobility Radeon HD 5800 series]
03:00.0 VGA compatible controller: ATI Technologies Inc Broadway XT [Mobility Radeon HD 5800 series]

---

### Post by RebateFX on 2011-05-25
> **Hakri said:**
> Here's what it says :

I have an M17x R2. Just use the driver suggested by Ubuntu's "Additional Drivers" tool. It works fine.

Just be aware that 11.04 doesn't seem as snappy as 10.10 was for ATI users. Make sure you tweak compiz. Go into the OpenGL settings in ccsm and turn off sync to vblank. Turn on the tear free option in catalyst instead.

---

