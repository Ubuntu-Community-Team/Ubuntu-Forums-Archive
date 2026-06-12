---
title: "Compiler for BASH scripts?"
date: 2008-10-05
forum: General Help
---

### Post by Tom Mann on 2008-10-05
Hi all,

As my title asks, is there a compiler for BASH scripts? For increasing the speed of one?

Also, if there were would we see any speed advantage in compiling the main startup scripts?

Cheers,
T

---

### Post by y-lee on 2008-10-05
There is a compiler, see [The Bourne Shell Compiler]("http://www.comeaucomputing.com/faqs/ccshdoc.html") for [The Bourne Shell]("http://en.wikipedia.org/wiki/Bourne_shell") (also known as sh) which is almost the same thing. It is my understanding bash differs some here and there from sh so this compiler may not work *with all* scripts without some modification of the script.

As to system startup, that involves lots of disk I/O and so on, which is pretty much the slowest thing you can do on a computer. Even if the script were much faster , it'd still spend most of its time sleeping. So the speed of bash and the script is unlikely to matter much.

---

