---
title: "install Python 2.6"
date: 2009-02-09
forum: Installation &amp; Upgrades
---

### Post by FraggedLocust on 2009-02-09
I'm installing Python 2.6 alongside 2.5. But I can't get 2.6 to run.

I've downloaded, unpacked, configured and made the default installation for 2.6. 

I'm guessing i need to put a path to the interpreter somewhere?

---

### Post by snova on 2009-02-09
Since you built it from source, it was probably installed in /usr/local- which is checked for commands last. Thus, typing **python** will run the version in /usr instead.

Try running it as **python2.6**.

---

