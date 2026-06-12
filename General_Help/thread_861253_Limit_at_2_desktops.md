---
title: "Limit at 2 desktops"
date: 2008-07-16
forum: General Help
---

### Post by idontknowwhy on 2008-07-16
I'm trying to get my compiz to work with more than 2 desktops (again).  Its a weird issue, when I first installed it, and enabled some effects, I had 3 desktops.  After enabling a few others, I have been limited back to 2 desktops.  Even if I disable all compiz effects, I can still not set my desktop number to higher than 2. (It resets it back to 2 whenever I try to add more desktops).  If I disable compiz entirely, I get back the ability to set more than 2 desktops.
What can I check?  There has to be some setting stuck somewhere...

---

### Post by overdrank on 2008-07-16
> **idontknowwhy said:**
> I'm trying to get my compiz to work with more than 2 desktops (again).  Its a weird issue, when I first installed it, and enabled some effects, I had 3 desktops.  After enabling a few others, I have been limited back to 2 desktops.  Even if I disable all compiz effects, I can still not set my desktop number to higher than 2. (It resets it back to 2 whenever I try to add more desktops).  If I disable compiz entirely, I get back the ability to set more than 2 desktops.
What can I check?  There has to be some setting stuck somewhere...

Hi and welcome, have you checked the general section in CCSM advance desktop settings? And also have a look at the link in my signature
VVVV

---

### Post by idontknowwhy on 2008-07-16
I figured this one out.  I was solely looking in the advanced settings for my answer.  Perhaps because there are so many settings, I could not find the one that would allow me to change the number of desktops.  

So, after a lot of frustration, uninstalling (and subsequently unable to boot back into kubuntu) then reinstalling, I tried the Compiz simple settings manager.  This was what was making the desktops stick to only 2 desktops.  (Under the desktop tab, change from 2 to x where x is the desired number of desktops).  Worked like a charm now.

Perhaps now I can get back to work.  :)

---

### Post by Vadi on 2008-07-17
Oops. Yes, the CCSM wasn't designed for normal users as they said, although it's being used like that simply because it's the most powerful tool about. For the future, General Options - Desktop Size - "Horizontal Virtual Size" determine how many viewports do you have.

---

