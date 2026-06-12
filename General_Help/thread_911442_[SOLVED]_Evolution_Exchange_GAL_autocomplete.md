---
title: "[SOLVED] Evolution Exchange GAL autocomplete"
date: 2008-09-05
forum: General Help
---

### Post by gen.alcazar on 2008-09-05
Hi Folks:

So I use Evolution 2.22.3.1 with the exchange plugin on Ubuntu 8.04.  I have GAL configured to point to my office domain controller, to which I have about 0.3 ms latency.  GAL is working - I can search for contacts and autocomplete works (well, almost!).

Here's the problem: at times, when I'm composing new mail and start typing a name in the "To:" field, Evolution freezes.  I can only guess that it is performing an LDAP query at the time.  The freeze usually lasts for about 30 seconds or so, sometimes more.  Is this something that others are experiencing too, or is this something that is unique to my environment that I need to explore further?

I should mention that the above situation occurs about 70% of the time, the other 30% of my efforts result in a quick response to autocomplete.

Thanks!****

---

### Post by gen.alcazar on 2008-09-05
bump!

---

### Post by gen.alcazar on 2008-09-06
OK.  Turns out the issue was specific to my setup.  A TCP dump told me that TCP was having a problem communicating well with the domain controller running on a... wait for it... windows server!  Changed Evolution to go to another local server, and works beautifully now.

---

