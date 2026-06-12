---
title: "Logitech MX3200 Keyboard + Ubuntu"
date: 2007-02-12
forum: Hardware &amp; Laptops
---

### Post by bunger2 on 2007-02-12
Hi Everyone: 

I recently purchased a Logitech MX3200 Keyboard (+ MX600 Laser Mouse) combo; the short version of my trouble is that I can't get any of the extra keys on the keyboard, or extra mouse buttons to work in ubuntu. 

I've done some research and there are several utilities (Keytouch, etc) that claim to be able to resolve this issue, but none of them seem to have any information on this particular keyboard/mouse combination. 

Additionally, there seems to be a kernel bug that can cause the multimedia keys to not output keycodes? 

Ultimately, I'm just wondering if anyone else has had experience with this and/or can give me some hints as to how to resolve this dilemma?

---

### Post by oolunchbox on 2007-02-12
I'm going to have to bump this as I have been eyeing this mouse keyboard combo for my fiancee but have been hesitant due to lack of support for the features.

---

### Post by bunger2 on 2007-02-13
I finally solved this problem. 

I returned the MX3200 back to the store. 

Long and short version is that nothing on that keyboard is guaranteed to work in Linux. Logitech simply won't provide drivers for it, and I'm not interested in spending untold hours trying to figure out why my extra keyboard buttons won't even generate events in xev. 

It might have something to do with a kernel bug, but I can't find any info at all on what you're supposed to do if the keypress doesn't -do- anything at all. Sure, if it generates a keycode, I can map that. But what if it doesn't? Driver problem, I assume. 

I read that there was more success with the MX5000, so I traded up for that one (at a 40 dollar increase, I might add). I managed to get the mouse working splendidly, but none of the fancy sliders or extra buttons will work with this keyboard either. 

Not blaming Ubuntu here at all, but I think this is kind of silly. I know it's logitech's fault for not releasing anything, not even an API, but you'd figure there would be some clue about how to fix this problem!

---

### Post by kelbizzle on 2007-02-14
I remember using a command that output the codes after you would push one of the extra buttons. Then I would just go and make it  a keyboard shortcut. I'm looking for the original thread it's how I found this one. Anyone remember that command?

---

### Post by bunger2 on 2007-02-14
> **kelbizzle said:**
> I remember using a command that output the codes after you would push one of the extra buttons. Then I would just go and make it  a keyboard shortcut. I'm looking for the original thread it's how I found this one. Anyone remember that command?

I know that 'xev' will do it; the problem is that those keys output nothing. Xev doesn't even chirp. 

Heck, the MX5000 series doesn't even work well in Windows -- talk about a more expensive -downgrade-. The mouse (MX1000) works like a charm, it's too bad that I'll have to return it with the keyboard, but I decided to replace it with the G15 (wired) gaming keyboard + a G7 cordless rechargable mouse. 

Take-home message: Don't buy Logitech wireless keyboards. Go for the wired stuff.

---

