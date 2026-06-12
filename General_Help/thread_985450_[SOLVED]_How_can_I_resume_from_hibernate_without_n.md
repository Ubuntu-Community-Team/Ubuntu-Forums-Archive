---
title: "[SOLVED] How can I resume from hibernate without needing to log in?"
date: 2008-11-17
forum: General Help
---

### Post by James Paige on 2008-11-17
I am setting up an ubuntu box for my Mom. Intrepid on a Thinkpad R60.

I have it configured to log in as her username automatically. That part works fine.

When I hibernate and then resume, it prompts for her password. How can I make it log in automatically just like it does for a clean boot?

(I couldn't figure out how to do this with Feisty either, but I didn't worry about i because I couldn't get hibernate to work reliably with feisty)

---

### Post by kerry_s on 2008-11-17
look in the screen saver settings section
or
in the configuration editor theres a section called power-manegment, uncheck the ask for password on resume.

---

### Post by James Paige on 2008-11-17
> **kerry_s said:**
> look in the screen saver settings section

If you are talking about the "Lock screen when screensaver is active" checkbox, it is already unchecked. I wouldn't have asked if it was that easy ;)

> **kerry_s said:**
> or
in the configuration editor theres a section called power-manegment, uncheck the ask for password on resume.

I'll check that thanks!

EDIT: Awesome! I ran gconf-editor. Then I went to apps/gome-power-manager/lock and I found a key named "use_screensaver_settings" which was unchecked. I checked it, and now it works as expected. Thanks for pointing me in the right direction! :)

---

### Post by kerry_s on 2008-11-17
> **James Paige said:**
> If you are talking about the "Lock screen when screensaver is active" checkbox, it is already unchecked. I wouldn't have asked if it was that easy ;)



I'll check that thanks!

EDIT: Awesome! I ran gconf-editor. Then I went to apps/gome-power-manager/lock and I found a key named "use_screensaver_settings" which was unchecked. I checked it, and now it works as expected. Thanks for pointing me in the right direction! :)

there should also be settings for " prompt from standby/hibernate " i usually uncheck those to just in case.

---

