---
title: "What Happened To My Machine?"
date: 2007-01-31
forum: Hardware &amp; Laptops
---

### Post by Indref on 2007-01-31
About a week ago something happened to my laptop.

I left a friend to use it for ten minutes. In that time, somehow, something went wrong and it hasn't been the same since.

It's slow, it freezes up, it's slow, it can't run any movies anymore at any FPS above 1, it's slow, and did I mention it's generally really laggy?

I thought it was a hardware issue. The battery warning light has been flashing ever since this happened. Even though the battery is fine.

But maybe, just maybe, there is a software fault.

If anyone has the slightest clue as to what happened, please post. I need ideas. I'm selling this laptop to buy a desky and I need this working to do that.

Please, any ideas at all. And no, I have no idea what my friend did. Or if he even did anything at all.

Lastly, if this thread is posted in the wrong forum, feel free to let me know/move it/flame me.

-IA

---

### Post by floke on 2007-01-31
You could try creating a new user account, and login to that one to see if there's any difference.
Unless your friend did dome serious mucking around as root then they will only have been able to change your settings; hence if you use a new user settings this might improve the problem.

If it doesn't, then it indicates that it might be something more than a software problem.
You could try running a LiveCD to see if that works at the right speed. This will provide further evidence as to whether the issue is software or hardware related.

---

### Post by Indref on 2007-01-31
Well, root access of any kind brings up the "woah hay gimme ur pw lol" screen and that would of stumped him.

Starting another account is an extremely good idea, I'll try that and post again.

Is there any kinda of system check I can run to see if my cpu is broken, or if my ram is working or something? The change was very sudden and dramatic. Not to mention the blinking battery light.

---

### Post by Indref on 2007-01-31
Nope. No luck. Still super dooper laggy and slow.

Any ideas from this point?

---

### Post by floke on 2007-01-31
Don't know of any system diagnostic tools - you could use the system monitor tool, which might show you if your swap file is working. There's actually an easier CLI way to do this, but unfortunately I don;t know what it is. I also think there's a thread somewhere about Ubuntu running slow, so I'd have a browse around. 
The only other thing I can think of would be to delete all your .gconf and .gedit files so that gnome has to reconstruct them for your session - this will remove all info on your gnome sessions so you wil lose your desktop configuration - i.e. panel arrangements, wallpapers, icons etc. - so it's a bit of an extreme move, usually recommended for when people can't log in to their sessions.

Sorry not to be of any more help - the use of the LiveCD will probably be a key clue - if that runs slow then its hardware related.

---

### Post by glabouni on 2007-01-31
> **Indref said:**
> Is there any kinda of system check I can run to see if my cpu is broken, or if my ram is working or something? The change was very sudden and dramatic. Not to mention the blinking battery light.

to test your ram you can use memtest which should be available in grub boot menu.
try from ubuntu live cd if it's not.

from what you've described, if you have no other lead to investigate, I throw an idea: it could be your computer switching to/stuck into an energy saving mode.


> **Steve.K said:**
> Don't know of any system diagnostic tools - you could use the system monitor tool, which might show you if your swap file is working. There's actually an easier CLI way to do this, but unfortunately I don;t know what it is. 

to monitor what's happening there's gkrellm (gui) or htop (cli)

> **Steve.K said:**
> the use of the LiveCD will probably be a key clue - if that runs slow then its hardware related.

or maybe a BIOS misconfiguration, although BIOS usually don't change by themselves

---

### Post by Indref on 2007-02-01
Ok! I played around and got some more info.

memtest came back clean, no problems
I ran the LiveCD. Things were pretty damn slow. But I seem to remember that the LIveCD ran pretty damn slow before I had this problem, so that doesn't help.

I've noticed that when I shut down the machine for about a minute, and then boot it again, it's back to it's cheery self. Then after a few minutes or an hour, it's slow as mud.

The machine may be stuck in some energy saving mode. I disabled any mode like that in the BIOS, no improvement.

I really am getting nowhere here.

---

### Post by floke on 2007-02-05
Have you tried messing around with the power saving settings?
You could also try booting with 'no acpi' (not entirely sure how - athough I'm pretty certain you can - but best have a browse around the forum) - I think this boots up without power management detection - if so, and it's stil slow then you could probably rule that out.

It does sound like a hardware problem though - would a different user account share the same power settings? If not, then it can't be that since you tried a different user earlier. Also , can you dual boot - how does Windows work?

Also - you could try a fresh reinstall - last resort I know but if you back up all your data then at least it only takes 20-30 mins. 
If its still slow then, then its a hardware issue for sure!

---

