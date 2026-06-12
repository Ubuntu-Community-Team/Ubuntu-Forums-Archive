---
title: "Have problems when compile ckpt"
date: 2008-08-21
forum: General Help
---

### Post by sst on 2008-08-21
When I compile ckpt [http://pages.cs.wisc.edu/~zandy/ckpt/](http://pages.cs.wisc.edu/~zandy/ckpt/) then I have problem
```

phchon@phchon-laptop:~/ckpt$ make
gcc -Wall -g  -c mem.c
mem.c: In function ‘call_with_new_stack’:
mem.c:291: error: ‘JB_SP’ undeclared (first use in this function)
mem.c:291: error: (Each undeclared identifier is reported only once
mem.c:291: error: for each function it appears in.)
make: *** [mem.o] Error 1
phchon@phchon-laptop:~/ckpt$ 

```

Could you help me to fix them. Thanks!

---

### Post by fahadsadah on 2008-08-21
Have you installed the neccessary packages?
```
sudo aptitude install build-essential
```

---

### Post by sst on 2008-08-21
it doen't still work!

---

### Post by sst on 2008-08-28
Please help me! I tryed a lot of time, but it doesn't work.

---

### Post by cariboo on 2008-08-28
Did you try this:

[http://pages.cs.wisc.edu/~zandy/ckpt/woody](http://pages.cs.wisc.edu/~zandy/ckpt/woody)

Ubuntu isn't based on woody, but etch.

Jim

---

### Post by sst on 2008-08-28
I'm using Ubuntu-8.04. I don't know it is based on woody or not. How to fix it?

---

