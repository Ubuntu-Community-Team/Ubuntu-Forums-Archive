---
title: "[SOLVED] Conky has a shadow in 8.10 intrepid"
date: 2008-10-31
forum: General Help
---

### Post by ddarsow on 2008-10-31
I upgraded to 8.10 without any issues. The only thing which seems to have been affected was that Conky now has a shadow (from my emerald theme) which was never there before.

Aside from 8.04 to 8.10, nothing changed. I am attaching a screenshot of my desktop.

Any ideas? I prefer it without the shadow on Conky.

Oh well, I am very pleased with the smooth upgrade anyway! :)

---

### Post by conundrumx on 2008-10-31
In CCSM there is a "window decroation" plugin.  In there you can change the windows which get shadows or decoration.  Just click on the add button, then click "grab" and click on your Conky section.  Make sure the grab makes sense (so you don't just apply settings to your desktop or something) and then check the "invert" box.

That will do it.

---

### Post by sanus|art on 2008-10-31
or maybe change 'own_window_type normal' to 'own_window_type override' in .conkyrc

---

### Post by ddarsow on 2008-10-31
> **sanus|art said:**
> or maybe change 'own_window_type normal' to 'own_window_type override' in .conkyrc

Thats the ticket!
Thanks for the prompt and useful reply.
Dave

---

### Post by agentnixon on 2008-11-01
I can confirm that the CCSM method works. There's some neat tweaks worth looking in there, too.

---

### Post by madchine on 2010-05-05
to be explicit: "!class=Conky" excludes Conky in Compiz

---

