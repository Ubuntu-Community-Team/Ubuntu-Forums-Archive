---
title: "Java web plugin not working"
date: 2008-08-07
forum: General Help
---

### Post by artanis00 on 2008-08-07
Recently I tried to get the java web plugin to  work in firefox, and I ended up trying almost every solution I could find.

In firefox, it still doesn't work, but I found that when I installed Epiphany it did. So I was fine using firefox for browsing and popped over to Epiphany for java.

Until just now. I had updates so I let them install, and I saw a few java packages go by and now java doesn't work in Epiphany either.

I probably have several java packages installed by now and have no idea what to do to get this working.

I apologize for the lack of information in this post. I have subscribed to this thread, so I will try to respond to requests for information as quickly as I can.

Your assistance is greatly appreciated.

---

### Post by alzie on 2008-08-07
You don't provide alot of information but I think I see where you are coming from.

I'd suggest opening up Synaptic Package Manager and doing a search for java.

Mark all instances of icedtea-java for removal.

Mark sun-java6-plugin OR sun-java5-plugin for installation.  This should automatically pull the appropriate sun-java#-bin and sun-java#-jre with it.

(I'm currently using sun-java5 because I've had problems at some flash sites with sun-java6.)

You should also check that you have "ubuntu-restricted-extras" installed too.

I hope this helps.

I'm running Firefox 3 on Hardy Heron and these settings are working for me.

---

### Post by tuxxy on 2008-08-07
Have you tried Opera thats a good replacement, or you could type ```
about:plugins
``` into you firefox address bar and see what plugin you have infact got installed for web java

---

### Post by artanis00 on 2008-08-07
> **alzie said:**
> You don't provide alot of information but I think I see where you are coming from.

I'd suggest opening up Synaptic Package Manager and doing a search for java.

Mark all instances of icedtea-java for removal.

Mark sun-java6-plugin OR sun-java5-plugin for installation.  This should automatically pull the appropriate sun-java#-bin and sun-java#-jre with it.

(I'm currently using sun-java5 because I've had problems at some flash sites with sun-java6.)

You should also check that you have "ubuntu-restricted-extras" installed too.

I hope this helps.

I'm running Firefox 3 on Hardy Heron and these settings are working for me.

Ah yes, that did it. I can't believe I didn't think about that...

Thank you very much.

---

