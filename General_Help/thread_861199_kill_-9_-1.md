---
title: "kill -9 -1"
date: 2008-07-16
forum: General Help
---

### Post by sulekha on 2008-07-16
Hi,

I was going through the book "Hacking Ubuntu" by Neil Krawetz

in this book it is said that never do kill -9 -1 as root.

in my office i tried this command as root on an RHEL4 machine

but there was'nt any system crash as i expected only the x-server got crashed, and the commands like ps, ls were n't giving any o/p.

my question why init process wasn't killed ?

---

### Post by evets25 on 2008-07-16
My guess would be it's because Ubuntu has shifted away from the traditional init system and moved to something called "upstart." If you're interested in learning more about it, there's a great article on it [here]("http://www.linux.com/feature/125977").

---

