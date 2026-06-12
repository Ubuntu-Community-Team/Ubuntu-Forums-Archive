---
title: "Avant window navigator problem?"
date: 2008-09-08
forum: General Help
---

### Post by Redp on 2008-09-08
Well, I don't quite know what to make of this one. I've just installed awn, and I'm having some issues on session startup. Before I go on, I'd like to apologize in advance if this has been answered before - I did a search for this problem before posting, but could not find anything. Anyway. For those who want to skip my lengthy explanatory babbling about the problem, I've summarized it at the end of the post.

So I've installed awn and it went fairly well to set up everything. Then, I ended up having to reboot my computer because of some other thing - nothing major, just a game that didn't run properly. Ubuntu loads, I log in and ... nothing happens. Or almost nothing. The desktop image comes on, but the mouse cursor does not load properly, and instead there's an X. Great. I wait for a minute or so, nothing new happens, so I physically power off the computer by pressing the power button. I know, that's a bad idea generally, but I did not know what to do, and nothing seemed to respond (keyboard was unresponsive, as was the mouse - I could move the cursor, but clicking didn't do anything). 

I power the computer back on. Ubuntu loads, I log in and everything works. I spend a bit of time on the comp, shut it down normally, everything goes smoothly. Then, a few hours later, I power the computer up, Ubuntu loads, I log in and... same problem. Cannot anything but to hold the power button on the laptop to turn it off. I turn it on again, and everything loads properly.

I reboot the computer properly, and it hangs on log in. Power it off physically again, and back on, and everything loads fine. I did this a few times. I don't know what's going on. Everytime I either log out, restart or shutdown the computer properly, the next time I reboot, my session never finishes loading. Everytime I need to turn it off by force, the next time I boot it up it works fine. 

I should mention again that the problem started following my installation of awn. I've tried delaying awn startup on login by a few seconds by going into the Sessions manager, because I thought that maybe I ought to give more time for compiz to load before letting awn load. That didn't work. I'm a bit at a loss as to what I should do. 

Sorry about the lengthy explanation. Could be summarized this way:

[I]- My GNOME session does not load properly if I'm starting the computer after turning it off, rebooting it or logging out properly;
- It does load properly after I turned it off, etc.
- The problem seems to be linked to awn.[/I]

Also, dunno if it matters, but I'm using Hardy Heron 8.04, on a Toshiba laptop (1.66 ghz, intel integrated graphics, 2 gig of ram).

Do you guys have any ideas on how to solve this thing?

Thanks in advance

P

---

### Post by TheUbGuy on 2008-09-08
The only thing I can think of off the top of my head is, once you do get into your 'normal' desktop, go to Synaptic Package Manager, do a search on Awn, and completely remove it. Then shutdown and restart and see if that helps. If it does, then it is definitely linked to AWN.

---

