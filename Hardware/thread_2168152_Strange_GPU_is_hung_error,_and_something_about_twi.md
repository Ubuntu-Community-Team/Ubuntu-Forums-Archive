---
title: "Strange GPU is hung error, and something about twitter?!"
date: 2013-08-16
forum: Hardware
---

### Post by tJCyFFh on 2013-08-16
Aug 16 14:43:13 nsrdadowgail98 kernel: [ 1251.777725] [drm:i915_hangcheck_hung] *ERROR* Hangcheck timer elapsed... GPU hung
Aug 16 14:43:13 nsrdadowgail98 kernel: [ 1251.777733] [drm] capturing error event; look for more information in /debug/dri/0/i915_error_state
Aug 16 14:43:15 nsrdadowgail98 kernel: [ 1253.772715] [drm:i915_hangcheck_hung] *ERROR* Hangcheck timer elapsed... GPU hung
Aug 16 14:43:15 nsrdadowgail98 kernel: [ 1253.773004] [drm:i915_reset] *ERROR* GPU hanging too fast, declaring wedged!
Aug 16 14:43:15 nsrdadowgail98 kernel: [ 1253.773009] [drm:i915_reset] *ERROR* Failed to reset chip.
Aug 16 14:43:17 nsrdadowgail98 gnome-session[2034]: WARNING: App 'gnome-shell.desktop' respawning too quickly
Aug 16 14:43:17 nsrdadowgail98 gnome-session[2034]: CRITICAL: We failed, but the fail whale is dead. Sorry....

This is happening all the time. In Unity, it seemed to happen every time I moved a window across monitors. Everything froze, I had to turn off and on my laptop. I replaced Unity with Gnome 3.8. Same thing, only this time, the result is that I no longer have the gnome interface, and all opened windows lose their borders / decoration. Again, only solution is to turn off and on the laptop.

I am also not sure what gnome-session is going on about. "fail whale is dead"?? Isn't the "Fail Whale" a twitter thing? I am not using Twitter anywhere. Maybe I'm being trolled :(

Any ideas what is going on here?

---

### Post by Ranko Kohime on 2013-08-16
The fail whale is the developers trying to be funny, about something.  (Yay for obscure error messages)

I never experienced it with Unity, but both Gnome 3 and Cinnamon would hang on me fairly frequently, enough so that I had to eventually drop them.

---

### Post by tJCyFFh on 2013-08-21
so what about this hung GPU?

This is a recent problem. Is it gnome related or do I have an actual hardware fault? how can I figure it out?

---

### Post by Ranko Kohime on 2013-08-24
That I'm afraid I can't answer, as I've never seen it before, and don't know what it means...  But here's a free bump so it may hopefully be seen by someone who does.

---

