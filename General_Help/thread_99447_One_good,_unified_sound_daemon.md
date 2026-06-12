---
title: "One good, unified sound daemon"
date: 2005-12-05
forum: General Help
---

### Post by outdooricon on 2005-12-05
I've been messing around with the different sound daemons (esd, alsa, etc.). I'm wondering, why can't we just have one sound daemon, that everyone focuses on using and leave it at that. Why are there so many different options,e ach with different strenths? Is it moving towards one? I thought ALSA would be the one, but It seems to suck (plays video choppy, mozilla-plugin streaming is choppy too, also crackles my music). What is the deal with all of this? NOTE: I am not asking how to fix poblems but am rather opening a discussion on this.

---

### Post by Gray. on 2005-12-05
Well I might as well join in. :) I too think that it would be good to have one unified sound daemon, but I **think** the main reason that it won't be so for a while is because they have to keep support for older hardware. I would really love for the GUI on Linux to be hardware accelerated (read: rendered by the video card) to make it more responsive (I don't really care too much about the flashy effects, just give me stability and speed).

---

### Post by dbindner on 2005-12-05
[QUOTE=Gray.]Well I might as well join in. :) I too think that it would be good to have one unified sound daemon, but I **think** the main reason that it won't be so for a while is because they have to keep support for older hardware.[/QUOTE]

Having done a little sound programming myself and looked through the source of and comments of other sound programmers, I think it will be a long time if you're hoping for ALSA to be the common solution.  The lack of documentation in ALSA is profound.

I found it completely perplexing.  Open source people usually do their work out of love and hope to have their software used and appreciated.  Who would write an extensive library and not document it?  Don't you want programmers to use your software?

---

### Post by nalmeth on 2005-12-06
Yes, I would be in favor of a New Sound Order, but I think the reason it isn't here yet, is because indeed they all have their own strengths, and probably incompatibilities, but more than that, it is so easy to interchange between systems. If you run into problems, there are usually easy ways to solve them, if not there are forums and other net-places to find answers. Maybe there is not a lot of ALSA documentation, and I can't comment at all about that, but I've never had a problem that someone else hasn't had already. Maybe I'm just lucky:) 
Granted there are still circulating issues, and in general linux sound is far from perfect, *other* unified systems out *there* are eons from perfect, and I'm glad to know that if my current system doesn't do it for me, there's another that might.
I think its great that there are many major sound systems, each with differences that might or might not cater to each individual. 
I'm sure one day an all-encompassing all-powerful sound daemon will emerge with support for every user new and old, but until then, considering my lack of conflicts/problems, I'm satisfied with our current state of affairs. :D

---

