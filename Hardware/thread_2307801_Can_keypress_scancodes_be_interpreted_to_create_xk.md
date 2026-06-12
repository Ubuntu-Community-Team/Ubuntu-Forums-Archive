---
title: "Can keypress scancodes be interpreted to create xkeybindings?"
date: 2015-12-28
forum: Hardware
---

### Post by egeezer on 2015-12-28
A while ago I reconfigured two of the buttons on a gaming mouse to give me Copy and Paste at the file and folder level in Thunar.  I did that by getting button numbers from xev and reconfiguring their function with xbindkeys.
 
 
 I'm trying to see if I can do something similar with two of the extra keys on an old eMachines keyboard.  The keys are designated Copy and Paste and probably did exactly that back in the days of XP, but they do not record any signal when I test them on xev.   
 
 
 I installed and ran evtest, which gave me the scancodes for them, but hexadecimal event codes are not workable as xbindkeys configuration entries, the way button press numbers are for a mouse.  Is there some intermediary translation from scancodes to X-readable entries, perhaps in systemd, or is it a matter of changing something at serious kernel level?  If it does go that deep, I probably wouldn't do it – after all, it's only to get a fast way to copy and paste files from place to place.
 
 
 For reference, I'm running Xubuntu Core 15.10 at the moment, with limited software added.

---

