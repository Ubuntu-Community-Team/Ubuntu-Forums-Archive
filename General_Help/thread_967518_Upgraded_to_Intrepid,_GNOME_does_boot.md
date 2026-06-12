---
title: "Upgraded to Intrepid, GNOME does boot"
date: 2008-11-02
forum: General Help
---

### Post by BobtheBlueBerry on 2008-11-02
Hi. I just upgraded from Hardy to Intrepid after days of downloading installation files. After I finished upgrading and restarted my computer into Ubuntu, GNOME didn't boot properly. It just showed the uni-color background and did nothing. The root account does the same. Failsafe GNOME seems to work, as I'm on it now. Also, going into Failsafe Terminal and running 'gnome-session' will work. I've tried deleting config files and stuff, but nothing works.

Short story:
Upgraded from Hardy to Intrepid, [not]GNOME[/not]<<Xclient>> Session does not work for both my own and the root account. Failsafe GNOME works.

I have no clue what's going on. If you could help me it'd be great.

Thanks, Bob

---

### Post by BobtheBlueBerry on 2008-11-02
Wait.. It seems that "GNOME" session works, but not "XClient".
Perhaps it's my XClient script?
Does anyone know where that is located?


- Bob

---

### Post by billstei on 2008-11-02
I had this same problem... if you can get into fail safe Gnome, look in System->Preferences->Sessions->Startup Programs and uncheck any that you think might be problematic, then retest.

Bill

---

### Post by BobtheBlueBerry on 2008-11-02
I tried unchecking all of the start-up things and still the same thing.
I can get into GNOME Session, and the start-up programs run fine so I don't think they are a problem.

I can't get into root using XClient Script Session, so there's probably something wrong with the script, or some non user-specific file. Does anyone know where the script is?

- Bob

---

### Post by Kougaiji on 2008-11-08
I have the same problem, any solution yet?

---

### Post by BobtheBlueBerry on 2008-11-08
No, not yet. I have set my default session to GNOME rather than XClient Script.

---

