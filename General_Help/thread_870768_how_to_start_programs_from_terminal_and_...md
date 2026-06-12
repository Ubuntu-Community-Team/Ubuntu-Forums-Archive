---
title: "how to start programs from terminal and .."
date: 2008-07-26
forum: General Help
---

### Post by denarced on 2008-07-26
let's say I wanna view a document and I start evince to do so. How do I do it so that terminal doesn't get stuck. In other words. So that the terminal just starts the software and then gets back to denarced@denacomp:~$

---

### Post by natirips on 2008-07-26
> **denarced said:**
> let's say I wanna view a document and I start evince to do so. How do I do it so that terminal doesn't get stuck. In other words. So that the terminal just starts the software and then gets back to denarced@denacomp:~$
Add an & sign after the command.
```
$evince filename &
```

---

