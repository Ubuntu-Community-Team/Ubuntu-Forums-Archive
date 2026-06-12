---
title: "No keyboard/mouse input after Alt+SysRq+K in Jaunty"
date: 2009-05-26
forum: Installation &amp; Upgrades
---

### Post by Tiede on 2009-05-26
Hello all,
I just upgraded to Jaunty a couple of days ago and stumbled upon the Ctrl+Alt+Backspace removal "feature"...
So now, I am trying to use AltGr+SysRq+K to restart X, just testing, mind you, to feel confident that I'll have a way out if/whenever things go awry.
However, no matter how many times I try it, or when I try it, same thing always happens:
It logs me out of gnome, and restarts X, which restarts gdm (or at least it prompts me for a password)
At that point in time, my laptop stops responding, as far as the keyboard and the mouse are concerned. I can't even use Ctrl+Alt+F[1-8] to check/change anything.

My question is, how does AltGr+SysRq+K differ exactly from Ctrl+Alt+Backspace?
Could it be that it is killing some low-level program that is listening for keyboard/mouse input?

(the power button still works, i.e, shuts down the pc properly, or does whatever else I tell it to do ;) ) so I know it's not just COMPLETELY locked up...

Question is, anyone seeing this in Jaunty? (i got all the updates, bells and whistles)

My laptop is an Acer Aspire 3003WLMi.
To help out, any output that would help? lemme know, and I'll post it!
Thanks in advance for your help.

---

### Post by Tiede on 2009-05-27
so I guess nobody knows anything about the Secure Access Key?
I **know** they are different, because after reenabling Ctrl+Alt+Backspace with ServerFlag DontZap "False", i can break out of X and log in again normally, but the same does not happen if I try to use Alt+SysRq+K...

---

### Post by Tiede on 2009-05-29
hmm...
I'm surprised this issue hasn't rang a few bells.
Am I the only one affected by this? I'd like to know, so I can mark it on the bug report I filed with launchpad.
If you are reading this, would you please try the keyboard combination and see if this works for you...
**WARNING** *This will cause you to lose any unsaved data you may have at the time!*
Make sure all important data is saved before attempting this.

---

### Post by Tiede on 2009-06-07
Hmm... It's been a week and no body answers...
I'm starting to think this is just me, maybe...
Could somebody (anybody) just test it out and tell me what happens?
If you happen to be on a 32-bit laptop with a non-3d enabled card, that would be perfect. but at this point, any input would do...
Please, and thanks in advance.
I need to figure out if this is just me so I can no what to do to move forward.

---

### Post by enzyme on 2009-06-19
I checked on my laptop with an external USB keyboard and both the keyboard and mouse still work following Alt+SysRq+K in jaunty.

Cheers.

---

### Post by Tiede on 2009-07-06
Thanks for your reply, enzyme.
Fortunately for me, the issue has been resolved for me by a kernel update last month.
It edited my xorg.conf without warning and took out my "Don't Zap" workaround, but it now works...
I'm not entirely sure what the problem was. But hey, "if it ain't broke,..."!
Again thanks  for trying it out.

---

