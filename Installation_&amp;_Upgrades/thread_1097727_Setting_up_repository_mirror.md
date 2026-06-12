---
title: "Setting up repository mirror"
date: 2009-03-16
forum: Installation &amp; Upgrades
---

### Post by daniel_summers on 2009-03-16
I work for a "large government organization" doing software development.  We have gotten approval to use Linux for our development machines, and we have a couple of different levels of Ubuntu installed.  However, our over-zealous network folks have blocked most of the repositories (as they're categorized as "Software Downloads" - heh).

What I'd like to do is set up a mirror of the repositories on my laptop.  I can synchronize it from home, then let the other machines at work point to it for their updates.  Most of my searches point to apt-cacher, which would work great if the people don't have anything installed that I don't have.  However, it's not going to be able to go out to the main repositories any more than our current computers can now.

I'm thinking that the solution would involve rsync and an apt server, but I'd feel a lot better if there were a guide or something to follow - surely I'm not the first person to have this idea.  :)  If not, I'll work on it myself, and be sure to share what I find.

Thanks...

---

