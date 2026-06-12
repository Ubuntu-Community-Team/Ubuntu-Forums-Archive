---
title: "Still can't use emerald themes"
date: 2008-09-11
forum: General Help
---

### Post by kdarkentity on 2008-09-11
I have been working on my own custom o.s from quite some time now, however, i have stopped development for months due to the fact that i have not been able to use emerald themes. Is there anything anyone can do to help me?

---

### Post by kestal on 2008-09-11
What is your exact problem? :| I have had no problems with Emerald themes. Do they not want to change? Seeing as you did not include in the info, I will just assume the basic stuff happened. If you are using Compiz then you have to set the Window Decorator (in Advanced Compiz Settings and create a session through app menu->administration/preference/session) to 

emerald --replace


Can you describe your problem? -____-

---

### Post by TheUbGuy on 2008-09-11
> **kdarkentity said:**
> I have been working on my own custom o.s from quite some time now, however, i have stopped development for months due to the fact that i have not been able to use emerald themes. Is there anything anyone can do to help me?

Sorry, but you don't really give enough info for anyone to offer help. Maybe a few questions to get you going:

1. Is Compiz enabled and running ok?
2. You've installed Emerald (you should see the Emerald Theme Manager under System->Preferences)
3. What happens when you try to use Emerald (if all of the above are true)?

---

### Post by kdarkentity on 2008-09-11
Sorry on the lack of info earlier, yes compiz is running, and yes window decorations are enabled, and i still cannot use, apply or change emerald themes.

---

### Post by kestal on 2008-09-11
> **kdarkentity said:**
> Sorry on the lack of info earlier, yes compiz is running, and yes window decorations are enabled, and i still cannot use, apply or change emerald themes.

Thats odd..

and you changed the Windows Decorator (within Compiz) location to "Emerald --Replace" and set up a new Session with Emerald --Replace as the command already? (Plus a restart for it to kick in).

Go into your terminal and check to see if it works even. Type in "Emerald --Replace" there and see if your theme changes then. (Its only active while Terminal is open - the first things mentioned should fix if you didn't do that already).

**[COLOR="DarkRed"]--- Edit ---[/COLOR]** 

I am pretty sure to get the effect you want, you have to set up "emerald --replace" in both the Window Decorator within Advanced Compiz, aswell as creating a session by going to the Gnome-menu, administration (or preferences - do not remember which), then sessions.

(clicking new in the session screen)
Name: Emerald
Command: emerald --replace
Details: Emerald Theme Manager

---

### Post by kdarkentity on 2008-09-11
Hmm... i've tried restarting compiz several times in the past but foolishly never tried a emerald --replace. I'm gonna go try that and repost the result, thanks

---

### Post by joshuachad on 2008-09-11
hopefully that works

---

### Post by infinit1 on 2008-09-11
Sweet deal, that worked for me!

---

### Post by kdarkentity on 2008-09-12
Ok so here's the deal, if i run emerald --replace that enables the emerald themes and all is well, however at the start of a new session compiz is running but it's using the metacity themes still. How can i get emerald themes to start at the beginning of each new session?

---

### Post by kdarkentity on 2008-09-12
Nevermind, i added a start-up entry command "emerald --replace" and thats working so i guess i'm all set. Thanks.

---

