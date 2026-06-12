---
title: "[SOLVED] Ctrl-C Terminates Script"
date: 2008-10-04
forum: General Help
---

### Post by weasello on 2008-10-04
Hi there,

I have a script.

```

run_program_a
run_program_b
run_program_c

```

When I run it, a terminal window opens. It executes program A, which self-completes, and moves on to program B. This is where the problem occurs.

Program B is an infinitely-running program that has to be manually stopped. The keystroke to do this is Ctrl-C, and there is no other keyboard shortcut for this utility to make it terminate.

The problem is, if I hit Ctrl-C to terminate the utility, it actually terminates the entire script, and program C is never executed!

I read somewhere that encompassing it in brackets will run it in a sub-shell but that didn't seem to alter anything:

```

run_program_a
(run_program_b)
run_program_c

```

Any help on this would be great!

---

### Post by weasello on 2008-10-05
Hmm, turns out this was an artifact of running the script from Gnome Launcher as "gksudo". Changing this to "sudo" repaired it. Interesting!

---

