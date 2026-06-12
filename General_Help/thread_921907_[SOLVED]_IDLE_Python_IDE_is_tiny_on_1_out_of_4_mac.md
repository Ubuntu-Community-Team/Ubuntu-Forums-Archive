---
title: "[SOLVED] IDLE Python IDE is tiny on 1 out of 4 machines"
date: 2008-09-16
forum: General Help
---

### Post by clever on 2008-09-16
I installed IDLE, the IDE for Python programming language.  On this particular machine, the window and font are absolutely tiny.  But on three other machines, it looks fine.

The attached screenshot is how it looks when it claims to be using courier, 9 point font.  Each letter uses only a couple pixels!

The max font size I can select is 22 point, and that is still way too small.  Does anyone know why it is so small (and only on this one particular machine)?

---

### Post by clever on 2008-09-19
Well, this isn't a very satisfying solution, but here's what I did in case it helps someone:

I edited ~/.idlerc/config-main.cfg like so:
```
[EditorWindow]
font-size = 40

```

That's right -- I told it to use a 40 point font and the result is that it looks like it's using a 14 point font.  I still have no idea why it seems to be scaled so small on this machine.

---

