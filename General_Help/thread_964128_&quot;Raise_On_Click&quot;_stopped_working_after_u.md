---
title: "&quot;Raise On Click&quot; stopped working after upgrade to Intrepid"
date: 2008-10-30
forum: General Help
---

### Post by CharlieM on 2008-10-30
Hi All,

I have just upgraded my machine from Hardy to Intrepid and all has gone well except for one really annoying issue I can't seem to solve.

The "Raise on Click" option in Compiz Settings Manager has stopped working. It supposed to make a window raise to the top and grap focus if you click on any of its body. At the moment I can only do this through Alt-Tab or by click on the windows title bar.

Its as if it forgets this option. If I clear the check box and set it again in the Compiz Settings Manger, it works the first time I click on a window then it stops working again.

Is anyone experiencing the same thing or know of a possible solution?

Charlie M

---

### Post by mikeh on 2008-12-01
I googled the problem, and all i found was this post :-(

---

### Post by Forlong on 2008-12-01
Could you please be a little more elaborate on how it behaves right now and what you want to achieve?

---

### Post by mikeh on 2008-12-01
Certainly. I have installed Ubuntu intrepid with Compiz and selected focus-follow-mouse. ie "select windows when the mouse moves over them" in the GUI settings.
Since the dawn of time, clicking on a window would raise it, but now it only works if i click on the frame or title bar.  I would like to know how to change it back to the old behaviour. thanks.

---

### Post by Forlong on 2008-12-01
Hm... works here as expected.
You could try changing the backend to Flat-file in ccsm &#8594; Preferences

---

### Post by mikeh on 2008-12-01
> **Forlong said:**
> You could try changing the backend to Flat-file in ccsm &#8594; Preferences
Yep, that fixed it, at least after restarting compiz. So its a problem with the new front-end?
I see that a number of the options in ccsm->general->focus&raise are coloured blue, if the GConf backend is used. What does that mean?

---

### Post by Forlong on 2008-12-01
> **mikeh said:**
> So its a problem with the new front-end?
Well, like I said, on my machine it works as expected. 
> **mikeh said:**
> I see that a number of the options in ccsm->general->focus&raise are coloured blue, if the GConf backend is used. What does that mean?
Those options get parsed from Metacity (GNOME's usual window manager).

---

### Post by mikeh on 2008-12-01
Thanks.
So the question remains - how do I correct my bad settings?
... never mind, "rm -rf .compiz .metacity" and logout/in seems to have done the trick.

edit: ... and NO. When come back from hibernate it has broken again. :-(

---

### Post by chk9 on 2009-08-08
For those who stumbled on this thread.

I found a solution in the **gconf-editor**:
> 
/apps/metacity/general/raise_on_click


Hope that helps.

HF :D

---

