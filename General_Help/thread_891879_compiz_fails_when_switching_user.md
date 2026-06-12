---
title: "compiz fails when switching user"
date: 2008-08-16
forum: General Help
---

### Post by patmalcolm91 on 2008-08-16
Hello. When i switch users in any way (the applet, the quit screen, after locking the screen) with compiz running to another user using compiz, compiz crashes on that user, and the desktop reverts to metacity.

My laptop is a Dell Inspiron 630m with an intel 915 integrated graphics card and 1GB RAM.

I've noticed that one open desktop with a few applications uses around half or a little over half of my RAM, meaning two would go over the 1GB. Is this a RAM-related problem? shouldn't the old session be pushed to swap (or as much of it that needs to be)?

Is this a compiz problem?

I've searched everywhere, but any thread referring to this bug has no solution, and it appears that it is not very common, yet i've had this problem on both of the two laptops i've installed ubuntu on. The other is a Gateway with the same/similar intel GMA graphics card. not sure about the RAM on that laptop though.

Thank you in advance for any help you can provide.

---

### Post by Sam Lars on 2008-08-16
I heard that compositing/direct rendering/compiz only works for the first user logged in.

---

### Post by patmalcolm91 on 2008-08-17
i tried switching users and running "glxinfo | grep direct" and it did indeed say that direct rendering was off.

My next questions would be:

Is this a bug? If so, with what package? Is it filed/being worked on?

Does everyone, even with more RAM or better graphics cards, have this problem?

Is there a workaround available somewhere?

If anyone can answer any of these questions, it would help me greatly in finding a solution. Thank you in advance.

---

