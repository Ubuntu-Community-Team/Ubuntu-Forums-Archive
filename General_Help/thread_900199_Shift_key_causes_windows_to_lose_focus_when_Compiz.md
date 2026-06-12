---
title: "Shift key causes windows to lose focus when Compiz is enabled"
date: 2008-08-25
forum: General Help
---

### Post by JFire on 2008-08-25
Running a fresh install of Hardy 8.04

I thought id share this fix with you just incase anyone else is having similar issues.

On a fresh install of Ubuntu 8.04 and after updating, it seems that Compiz causes the shift key to act a little weird. Pressing it will cause your currently focused window to lose focus, meaning you won't be able to type capital letters or any special characters.

I fixed it by installing 'compizconfig-settings-manager' then disable the Keybinding located at: "General Options -> Commands -> Run command 0"

By default it is set to <shift><F19> (I've never seen a keyboard with an F19 button... )

Resetting or disabling this Key-binding solves the problem.

---

### Post by Graham1982 on 2008-10-08
Thanks JFire!  This happened after I mapped Run Command 0 to a program.  After a reboot it seemed to have changed to F19.  I wouldn't have through to look there!

I checked every plug-in and the general bindings but didn't think to look there, and probably wouldn't have before getting a bit more frustrated!  At least frustrated enough to have to google the problem.

Cheers!

---

