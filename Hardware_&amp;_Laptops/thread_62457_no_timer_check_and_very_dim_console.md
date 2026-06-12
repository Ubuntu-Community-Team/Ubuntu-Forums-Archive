---
title: "no_timer_check and very dim console"
date: 2005-09-04
forum: Hardware &amp; Laptops
---

### Post by matdoc on 2005-09-04
Hello,

I have a zv6000 series HP Notebook with a AMD64. Because of the fast hardware clock problem (clock runs at double speed), I installed the current milestone of breezy, which comes with the 2.6.12 kernel. With this, I can pass the no_timer_check option as boot parameter and this fixes the clock problem. But as usual - fixing one problem brings up another one. Now, whenever I switch to a virtual console, it is almost dark, but not completely dark, the letters are still somewhat visible, but very very dim. When I don't give the no_timer_check option, the console is just normal (but the clock runs at double speed - as I might have mentioned before). Does anybody know this problem or have a clue, what this could be? (I read about somebody having the same problem before I encountered it and now I can't find it again.)

Any help appreciated,

Mat

---

### Post by matdoc on 2005-09-04
Something just came to my mind:
When I read about that problem before, someone wrote, that it is some kind of acpi problem and somehow the display thinks that the machine is in the process of shutting down and is therefore dimming the display. But I can't remember the solution to the problem (if there was one). I already tried noacpi and acpi=off as boot options, but it didn't do the trick.

---

### Post by jnthnjng on 2005-09-30
I have exactly the same problem.  Has anybody around here found a solution?

---

