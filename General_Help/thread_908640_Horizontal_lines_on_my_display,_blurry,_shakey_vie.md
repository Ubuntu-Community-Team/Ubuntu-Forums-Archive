---
title: "Horizontal lines on my display, blurry, shakey view"
date: 2008-09-02
forum: General Help
---

### Post by carl99fan on 2008-09-02
Yesterday I installed a video game demo in wine.
It ended up being in a window so I could not use my mouse.
So I restarted the unit, and upon restart my screen has been all messed up ever since.
Just to be sure I just switched monitors and I still have the same problem.
I don't see anywhere I can change or review the settings.

Somebody, anybody please help this is terrible.
VERY unpleasing to the eyes kinda a strobing flashing effect going on as well.

---

### Post by carl99fan on 2008-09-02
# AMD Athlon 64 X2 4200+ 2.2 GHz processor
# 1 GB RAM
# 250 GB SATA hard drive
# Integrated video

---

### Post by carl99fan on 2008-09-02
I have uninstalled and reinstalled the Nvidia drivers and it's still there.
I did not see ANY lines in the signup screen......

Could this be the compiz fusion acting up!?

---

### Post by EmanresuusernamE on 2008-09-02
Sounds like your Wine got messed up somehow, have you tried playing with the display options of Wine, or reinstalling it?

---

### Post by carl99fan on 2008-09-02
> **EmanresuusernamE said:**
> Sounds like your Wine got messed up somehow, have you tried playing with the display options of Wine, or reinstalling it?

NO not at all I had No Idea WINE could do this...
I will check it out right now.

---

### Post by carl99fan on 2008-09-02
I will remove it...
I will use the package manager.

---

### Post by carl99fan on 2008-09-02
Used the package manager to "completely remove" both wine and wine-dev
Restarted, problem still there. :(

---

### Post by carl99fan on 2008-09-02
OK I found some wine stuff including a file called AGEIA physx

I would not be suprised at all if this is what got me cause it was installed with the game that toasted me. 
kill.switch ( DEMO )

using the terminal how do I remove all these files?

---

### Post by carl99fan on 2008-09-02
Your not going to believe this, I was tired of trying to fix this so I played enemy-territory and when I exited everything was back to normal.

WOW.

---

### Post by carl99fan on 2008-09-02
I restarted my computer and the problem returned.
the screen did not fit the monitor correctly and the lines were back.

SO I loaded ET again and quit game and BOOM my screen looks GREAT.

something must be configured wrong.

---

### Post by carl99fan on 2008-09-02
I typed in:

 gksu displayconfig-gtk

and I could see that the refresh rate was set at 50hz 
so I went to mt display settings and could see that it was set to 54hz

I moved it to 50, applied, restarted, and I am back in action.

working great.

---

### Post by EmanresuusernamE on 2008-09-03
:D Gotta love when it's simple.

---

### Post by wilcan34 on 2009-05-11
Had same prob.
Screen just would not settle down,blurry,shakey,too big pages for screen.
After seeing your post went to:System,Preferrences,Display and the setting was 60Hz and changed it to 56Hz and it looks as though it has settled down.
Knew if I searched long enough,and have for some weeks,I would find the answer.
Thank You for your Post.
Regards
W

PS. Solved

---

