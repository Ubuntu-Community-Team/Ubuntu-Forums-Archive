---
title: "dansguardian regular expressions not working"
date: 2008-08-17
forum: General Help
---

### Post by kung fu buntu on 2008-08-17
What I want to block:
hxxp://foobar.com/users/95461854--something_is_not_working
Because what follows "--" can change, I want to block everything that follows it:
hxxp://foobar.com/users/95461854--*

I was able to do this by addind the following line in /etc/..../urlregexplist:
"(^hxxp://foobar\.com/users/95461854--(.*))"->"hxxp://foobar.com"

The problem is that regular expressions force me to "edit" the URL.
This forces me to redirect the user to somewhere... which raises suspicion.
I would like for dansguardian *not* replying the browser... this would make it seem like a timeout.


The same would for the URLs in /etc/dansguardian/lists/bannedsitelist
Which currently redirect to an "access denied" webpage :(


Any ideas?
Thank you.

---

