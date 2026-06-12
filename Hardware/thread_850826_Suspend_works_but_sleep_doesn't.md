---
title: "Suspend works but sleep doesn't?"
date: 2008-07-06
forum: Hardware
---

### Post by steveyeager on 2008-07-06
I have a variant of ubuntu 8.04 named eAR.  It did not suspend correctly until I found a few threads that suggested some modifications.  Now it suspends correctly.  However, I set the power management to blank the screen after 15 minutes and put the computer to sleep after 30 minutes when running on battery power.  It does blank the screen correctly but after I wait over 30 minutes, the computer lights are all on and are not as they would be if I had manually (and successfully) suspended the computer.  I try to awake the computer by moving the touchpad, but it does nothing.  The screen stays blank.

Is there a difference between suspend and sleep?  What can I try to resolve this?

---

### Post by sdennie on 2008-07-06
> **steveyeager said:**
> 
Is there a difference between suspend and sleep?

Possibly.  What are you using to suspend the machine manually?  I think Ubuntu will use the pm-utils command "pm-suspend" to suspend the machine which may not pickup changes you've made in more traditional places to change suspend options.

---

