---
title: "Lucid:  lose keyboard input capability randomly in firefox or empathy"
date: 2010-07-21
forum: Hardware
---

### Post by cupoange on 2010-07-21
every once in a while i find i can no longer type in any text field in firefox or in a chat window in empathy.  the only way to fix it is to quit firefox and reopen, or to open a new chat window.  anyone else have this intermittent problem??

---

### Post by Deadite81 on 2010-07-22
I had a similar problem.  My issues were (and still are if I use it) caused by Compiz.  If I map any command to the right mouse button, say, right-click the bottom left corner for Expo or right-click the corners for the Put plugin (to tile windows), whatever window had focus would loose the ability to be typed in.

This happens to any window, not just Firefox and Empathy.  I did not have to restart anything though.  If I focused another window then refocused the affected window I could type again.  It's very annoying, so I just don't map anything to the right mouse button anymore.

If you use Compiz perhaps this is the problem.  Otherwise I have no idea, but thought I'd throw it out there.  I'm pretty tired so I hope that this is understandable!  Good Luck :)

---

### Post by cupoange on 2010-07-22
ah....dreaded compiz.  thanks for the tip.  I'll check my mappings and remove anything unnecessary.  yeah i figured it happened in any window but on this laptop I use firefox and messenger 90% of the time so I only notice it in those.  come to think of it, it has happened when trying to restart, or in terminal before but obviously not as often.

I really hate that compiz causes all these weird problems and the only solution is to disable it...IMHO without compiz I find ubuntu pretty 'boring'.

---

### Post by simosx on 2010-07-22
> **cupoange said:**
> every once in a while i find i can no longer type in any text field in firefox or in a chat window in empathy.  the only way to fix it is to quit firefox and reopen, or to open a new chat window.  anyone else have this intermittent problem??

A user reported that they could not click with the mouse. If they performed a click with the touchpad (assuming you have a laptop), then the mouse would get enabled again. Do you get something similar to this?

---

### Post by cupoange on 2010-07-22
this has also happened to me before.  sometimes the touchpad gets "stuck" as well, it stays in a select mode and until i tap with it i can't type anything either.

---

### Post by simosx on 2010-07-22
> **cupoange said:**
> this has also happened to me before.  sometimes the touchpad gets "stuck" as well, it stays in a select mode and until i tap with it i can't type anything either.

As if someone right-clicked in some other window so the text input is captured there. And you need to send a click event to cancel out the right-click.

---

